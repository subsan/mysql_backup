MySQL_backup
============

Light script for backup your MySQL databases.

# Installation
1. Download script
2. Set permissions
3. Configure database parameters
4. Configure backup scripts
5. Set up cron job

###Install requirements

Ubuntu:
```
apt install tnftp
```

###Download script
Download script "mysql_backup" and "mysql_backup.d" folder (for example, in /usr/local/sbin/mysql_backup/)
Create local folder for save backup files (for example, /usr/local/sbin/mysql_backup/backup/)

or

```
git clone git@github.com:subsan/mysql_backup.git
```

# Configuration

## MySQL Settings

Database, backup filename prefix and system dir settings in mysql_backup file:
```
# prefix of archive file
PREFIX="mysql"
# backup dir
BACKUPDIR="/usr/local/sbin/mysql_backup/backup"
# mysql access
MYSQLUSER="root"
MYSQLPASS=""
MYSQLHOST="localhost"
# databases
# comment this string for backup all databases
#DATABASES="test"
```

## Backup scripts configure

This script is able to send backups to different services (FTP, mail, Amazon c3).
For each service, there is an executive configuration file in the folder mysql_backup.d

For example, if you want to store backups only on FTP, it is enough to keep the file "ftp" in a folder "mysql_bachkup.d" and set in it settings of access to FTP

If you want to save the configuration on different ftp then you need to duplicate the file "ftp" with a different name in the "mysql_backup.d" folder and configure it to another ftp server

## Crontab

Enter crontab -e and insert the following after editing the folders

```
1 2 * * * /usr/local/bin/mysql_backup/mysql_backup
```

@todo add information about install and configure amazon s3
