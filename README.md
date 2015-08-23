# innobackupex-s3

Utility scripts for encrypted incremental backups to amazon s3 based on [Streaming MariaDB backups in the cloud](https://mariadb.com/blog/streaming-mariadb-backups-cloud) and [original tappleby's innobackupex-s3 script](https://github.com/tappleby/innobackupex-s3).
 
The xbstream format is used for easy to manage backups. S3cmd is used to perform all operations with S3. Optionally, MySQL user/password can be set for the backup operation.
 
## Scripts

### innobackupex-s3-backup

Handles the incremental backups to amazon s3, 1 week of backups is also kept locally on the server.

Required environment variables:

- **S3_BUCKET**: S3 bucket where the backups will be uploaded
- **MYSQL_USER**: (optional) MySQL username
- **MYSQL_PASSWORD**: (optional) MySQL password

Optional environment variables:

- **BACKUPS_DIR**: full path where mysql backups will be stored on the server. 
- **KEY_FILE**: key file used for encrypted backups. use `innobackupex-s3-genkey` to generate key.  

### innobackupex-s3-restore-prepare

prepares a directory containing encrypted xbstream backups for restore. expects the first xbstream file in the directory to be a full backup.

Optional environment variables:

- **KEY_FILE**: key file used for encrypted backups. use `innobackupex-s3-genkey` to generate key.  

### innobackupex-s3-genkey

Generates a key file for use with encrypted backups.

Optional environment variables:

- **KEY_FILE**: override the default output file location. 
