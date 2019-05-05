# SQL Server 笔记

## 重启 sql-server
````bash
systemctl status mssql-server # 查看 mssql-server 的运行状态
systemctl restart mssql-server # 重启 mssql-server
systemctl stop mssql-server # 停止 mssql-server 服务
````
## SQL Server 进入单用户模式
````bash
/opt/mssql/bin/sqlservr -m -c -T7806 # -m 参数表示以单用户启动 SQL Server
sqlcmd -S localhost -U SA -P <Password> # 进入 sqlcmd
> sp_addsrvrolemember 'lolimay', 'sysadmin' # 将 lolimay 添加进管理员用户组
> go
systemctl restart mssql-server # 重启 mssql-server 服务
# 或者
 sudo nohup /opt/mssql/bin/sqlservr > /dev/null 2>&1 &
````

## 数据库相关操作
````bash
create database experiment2; # 新建数据库
drop database experiment2; # 删除数据库
````

## 表格相关操作
### 表格
创建一个 Course 表
````sql
create table Course (
	Cno SMALLINT PRIMARY KEY,
	Cname char(20) UNIQUE,
	Cpno SMALLINT,
	Ccredit SMALLINT
)
````