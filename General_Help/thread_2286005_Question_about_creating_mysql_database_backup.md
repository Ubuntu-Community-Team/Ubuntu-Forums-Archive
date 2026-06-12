---
title: "Question about creating mysql database backup?"
date: 2015-07-09
forum: General Help
---

### Post by peter1897 on 2015-07-09
I want to create mysql database backup but i am not sure which files i have to backup. In mysql database directory  /var/lib/mysql/ there are these files:

```
4.0K drwx------  6 mysql mysql 4.0K 2015-07-06 14:19 .
4.0K drwxr-xr-x 51 root  root  4.0K 2015-07-06 13:58 ..
   0 -rw-r--r--  1 root  root     0 2015-02-07 17:50 debian-5.1.flag
 10M -rw-rw----  1 mysql mysql  10M 2015-07-06 14:13 ibdata1
5.0M -rw-rw----  1 mysql mysql 5.0M 2015-07-06 14:19 ib_logfile0
5.0M -rw-rw----  1 mysql mysql 5.0M 2015-02-07 17:50 ib_logfile1
4.0K drwx------  2 mysql root  4.0K 2015-02-07 17:51 mysql
4.0K -rw-rw----  1 root  root     6 2015-02-07 17:51 mysql_upgrade_info
4.0K drwx------  2 mysql mysql 4.0K 2015-02-09 18:46 phpmyadmin
4.0K drwx------  2 mysql mysql 4.0K 2015-07-04 19:29 test
4.0K -rw-rw----  1 mysql mysql    4 2015-07-06 14:19 ubuntu.pid
4.0K drwx------  2 mysql mysql 4.0K 2015-02-09 20:04 wordpress
```

If i want to make a backup of the wordpress database do i have to backup only the 'wordpress' database directory?

---

### Post by Jrmie_bellion- on 2015-07-09
You should use mysqldump. It will generate a .sql file that you can use later to instantly restore your database to the same system or another, without manually touching the mysql server files.

[http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/](http://www.thegeekstuff.com/2008/09/backup-and-restore-mysql-database-using-mysqldump/)

---

### Post by peter1897 on 2015-07-09
I tried to use mysqldump but it doesn't seem to work. When i execute the command it opens new command line with arrow in front:

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| phpmyadmin         |
| test               |
| wordpress          |
+--------------------+
5 rows in set (0.03 sec)

mysql> mysqldump -u root -proot wordpress > wordpress_backup.sql
    ->
    ->
    ->
    ->
    ->
```

Is this the right way to execute the command?

---

### Post by Jrmie_bellion- on 2015-07-09
You must execute it from the linux terminal, not from inside mysql.

Else, your syntax seems correct.

Have a nice day,

---

### Post by peter1897 on 2015-07-09
Thanks, from linux terminal it worked.

How can i schedule mysql backup to remote server with rsync? I want to setup one backup that should be run every five days and one backup that should be run every day. How can i do that?

---

### Post by mastablasta on 2015-07-09
for wordpress there is a nifty plugin called UpdraftPlus. It will do what you want and more using a nice interface. 

database backup doesn't backup the pics and such (if you have any).

---

### Post by peter1897 on 2015-07-09
UpdraftPlus looks like a good plugin, but my question is about rsync.

---

### Post by SeijiSensei on 2015-07-09
> **peter1897 said:**
> Thanks, from linux terminal it worked.

How can i schedule mysql backup to remote server with rsync? I want to setup one backup that should be run every five days and one backup that should be run every day. How can i do that?

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by peter1897 on 2015-07-09
Can someone confirm if these crontab commands are correct:

This command will run the backup every 10 minutes:

```
*/10 * * * * rsync -az mysqldump -u root -proot wordpress > wordpress_backup.sql
```

This command will run the backup every 2 hours:

```
0 */2 * * * rsync -az mysqldump -u root -proot wordpress > wordpress_backup.sql
```

This command will run the backup every day:

```
@daily rsync -az mysqldump -u root -proot wordpress > wordpress_backup.sql
```

This command will run the backup every five days:

```
0 0 * * 5 rsync -az mysqldump -u root -proot wordpress > wordpress_backup.sql
```

---

### Post by nerdtron on 2015-07-09
Nope. Rsync has similar syntax to copy commands.
```
rsync [options] <source file> <destination file/dolder>
```

So you'll need two sets of commands here, one to mysqldump, and then another to rsync (remote copy) the file to another server.
Say, you save the following to a file name /home/user/backup.sh script
```
 
#!/bin/bash
mysqldump -u root -proot wordpress > /tmp/wordpress_backup.sql
rsync -az /tmp/wordpress_backup.sql user@192.168.10.10:/path/to/backup/folder
```

Now that the backup.sh script is saved, you'll need to create a cron entry for it run on specified time like the following.
This crontab entry will run the backup every midnight.
```

@daily /bin/bash /home/user/backup.sh
```

BTW, rsync needs to have another a passwordless login setup from source computer to destination computer because you won't be able to type your password when it runs automatically.

The technique in testing cron entries is to run the command manually. If all is successful and requires no intervention, then chances are good that it will run successfully when you add it to crontab.

---

### Post by peter1897 on 2015-07-09
I made a mistake in my previous post. I meant to include only the mysqldump command. I was asking mostly if the dates setup is correct.

I created the backup.sh script with the mysql and rsync commands inside, but i am not able to start it. How can i start it manually to see if it is working? I tried this: **sudo ./backup.sh** but it doesn't work.

---

### Post by nerdtron on 2015-07-09
> I created the backup.sh script with the mysql and rsync commands inside,  but i am not able to start it. How can i start it manually to see if it  is working? I tried this: **sudo ./backup.sh** but it doesn't work. 

What is the error? Try it running manually like this:
```
 sudo bash backup.sh
```

Or if you like to see how the script executes each lines, try running with the -x option:
```
sudo bash -x backup.sh
```

---

### Post by peter1897 on 2015-07-09
The error i get when i run **sudo ./backup.sh** is: **sudo: ./backup.sh: command not found**

But these two commands are working and executed the script:

[B]sudo bash backup.sh
sudo bash -x backup.sh[/B]

Can you explain how including bash in front of backup.sh executes the script and also how this line in the script works: **#!/bin/bash**
I know almost nothing about scripting in linux.

---

### Post by nerdtron on 2015-07-09
When you use the symbol "./" you explicitly tell that the terminal to run/use "this file in this directory". In this case you run **sudo ./backup.sh** will run tell the terminal that in this current folder, there is a file with name backup.sh and I want to run it.
There are 2 requirements however in using this technique to run a script:
1. The file/script should be declared executable, example:
```
## this is a normal file:
kenneth@nerdtron:~$ ll -h sample.sh 
-rw-rw-r-- 1 kenneth kenneth 0 Jul  9 13:30 sample.sh

## This file will be declare executable
kenneth@nerdtron:~$ chmod +x sample.sh 
kenneth@nerdtron:~$ ll -h sample.sh 
-rwxrwxr-x 1 kenneth kenneth 0 Jul  9 13:30 sample.sh*
```
2. Inside the file, there should be a declared "shebang" or the **#!/bin/bash** on the 1st line of the file which will be used to determine what type of shell environment to run this script. In this example, the #!/bin/bash means that when you run **sudo ./backup.sh**, the terminal will use the BASH Shell to execute this script.



Now why does it run using **sudo bash backup.sh**?
Because you explicitly declared that BASH should run this file. Even if the file is not executable, the BASH shell will read this script and execute it.



So which one do I choose to run the script? **./backup.sh **or** bash ./backup.sh**
It depends. 
If you know that SHELL to be used for the script, then it's easier to run it using longer method. Some scripts are perl scripts, others are php scripts, mostly or bash scripts like this:
```
bash script.sh       ## BASH shell script
perl script.pl          ## PERL shell script
php script.php      ## PHP shell script
```
If the file has no file extension or you are not sure what type of shell script it is, then it is better to use the shorter method **./scriptfile** because this will cause the terminal to read the "shebang" inside the script and automatically launch the correct interpreter for the script. Be sure that the scriptfile is declared as executable when you use this method.

If you want to learn more about the command line, I recommend this very helpful and easy to read book. Download the free PDF copy: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by peter1897 on 2015-07-09
Thanks, for the detailed explanation!

---

