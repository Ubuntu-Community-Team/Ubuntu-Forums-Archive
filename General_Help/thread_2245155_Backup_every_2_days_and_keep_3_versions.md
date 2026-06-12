---
title: "Backup every 2 days and keep 3 versions"
date: 2014-09-21
forum: General Help
---

### Post by chris137 on 2014-09-21
Hi,
you probably have no idea what I want by reading the title but I could not explain it in a few words.
Here is what I want to do:
Start backup-script every two days (possible with cron) and keep three versions at any time.
So it will look like this:
[TABLE="width: 750"]
[TR]
[TD]1[/TD]
[TD]backup.day1[/TD]
[TD]create backup.day1
[/TD]
[/TR]
[TR]
[TD]3[/TD]
[TD]backup.day1, backup.day3[/TD]
[TD]create backup.day3[/TD]
[/TR]
[TR]
[TD]5[/TD]
[TD]backup.day1, backup.day3, backup.day5[/TD]
[TD]create backup.day5[/TD]
[/TR]
[TR]
[TD]7[/TD]
[TD]backup.day3, backup.day5, backup.day7[/TD]
[TD]create backup.day7, delete backup.day1[/TD]
[/TR]
[TR]
[TD]9[/TD]
[TD]backup.day5, backup.day7, backup.day9[/TD]
[TD]create backup.day9, delete backup.day3[/TD]
[/TR]
[/TABLE]
I hope you get the idea..

I honestly have no clue how to do that.
If i was running this on a server which is up 24/7 I would probably try it with loops and some variables which are increased at every run but since I will run this from my home-PC the script will be stopped everytime I shutdown.

This is the script btw:
```
#!/bin/sh
NOW=$(date +"%d-%m-%Y")
mkdir /path/to/backup/$NOW
cd /path/to/backup/$NOW
wget -rc --no-host-directories --user=user --password=password ftp://ftp.mydomain.net/ -P /path/to/backup/$NOW
exit
```

---

### Post by rbmorse on 2014-09-21
I _think_ backintime (from repository) will do what you want as far as scheduling and retaining sessions in the backup store. It's pretty flexible.  The part I'm not sure about is backing up to a network location. 

EDIT: just checked, Back in Time will handle both SSH and SSH encrypted to a networked file store. 

Bacula will most certainly do what you want, but there's a pretty hefty investment of time and effort in getting it's various constituent parts set up and configured.

---

### Post by sotiris2 on 2014-09-21
Check this [thread](http://ubuntuforums.org/showthread.php?t=2195496&p=12882235&viewfull=1#post12882235) (post #2) to see some backup functions.

---

### Post by Vaphell on 2014-09-21
you should rather use YYYY-MM-DD format, because the standard alphanumeric sort is also in chronological order. 
2014-02-01 > 2014-01-31 but 31-01-2014 > 01-02-2014

with that format you'd get 'last 3 items' for free.
using bash and its arrays:
```
$ ls -1
2014-09-11
2014-09-13
2014-09-15
2014-09-17
2014-09-19
2014-09-21
$ back=( * ) # save all items in an array, should be in alphanumeric order by default
$ for b in "${back[@]}"; do echo "$b"; done
2014-09-11
2014-09-13
2014-09-15
2014-09-17
2014-09-19
2014-09-21
$ for b in "${back[@]:${#back[@]}-3}"; do echo "$b"; done  # 3 last array elems = 3 newest
2014-09-17
2014-09-19
2014-09-21
$ for b in "${back[@]:0:${#back[@]}-3}"; do echo "$b"; done # N-3 first array elems = all but 3 newest
2014-09-11
2014-09-13
2014-09-15
```

or you could set a threshold to let's say 5 days which should filter out all but 3 items.

```
$ for b in *; do (( $(date -d "$b" +%s) < $(date -d 'now -5 days' +%s) )) && echo "$b  5+ days old" || echo "$b"; done
2014-09-11  5+ days old
2014-09-13  5+ days old
2014-09-15  5+ days old
2014-09-17
2014-09-19
2014-09-21

```

---

### Post by tgalati4 on 2014-09-21
There is *logrotate* that will keep the last 3 versions of a file.

```
man logrotate
```

> tgalati4@Mint14-Extensa /etc $ cat logrotate.conf
# see "man logrotate" for details
# rotate log files weekly
weekly

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here


Add your custom stuff to the bottom of the file and reboot.  The system doesn't know the difference between a log file and a backup.

You can back up daily or weekly by adding scripts to /etc/cron.daily or /etc/cron.weekly.  You will notice that *logrotate* is already included, so if you add the correct *logrotate* configuration, you will get rotating backups on a daily or weekly basis.  Every two days would take a custom cronjob.

---

### Post by chris137 on 2014-09-22
I already looked through your suggestions but they all seem pretty complicated to me.
I added Vaphell idea to change the date-format because he is right of course.
While looking for something different I came across this pretty easy solution which does exactly what I want (I think):
```
DEL=$(date +%Y-%m-%d --date '6 day ago')
rm -r /path/to/backup/$DEL
```
My script now looks like this:
```
#!/bin/sh
NOW=$(date +"%Y-%m-%d")
DEL=$(date +%Y-%m-%d --date '6 day ago')
mkdir /path/to/backup/$NOW
wget -rc --no-host-directories --user=user --password=password ftp://ftp.mydomain.net/ -P /path/to/backup/$NOW
rm -r /home/chris/BackupBoard/$DEL
exit
```
In crontab I added this line to run it every two days:
```
  0     0       */2     *       *       /backup.sh
```
Is that what I want or will I have to check your other suggestions again?

---

### Post by Vaphell on 2014-09-22
If it works, it works. Personally i'd still go with removing "older than" than removing "exactly 6 days ago". The difference is very small but let's say that for whatever reason your machine is down at the scheduled time. The date that was supposed to be purged will survive and will never be tested again, while removing "older than" is a self correcting mechanism.

You could use the all but the last 3 array approach or a bit of date arithmetic i showed earlier (fancier) or even go in a loop a bit back in time to really make sure eg the last 3 days to be killed are really really killed (a bit lame).

```
for n in 6 8 10; do rm -r /home/chris/BackupBoard/$(date -d "$n days ago" +%Y-%m-%d); done
```

All in all it would be a minor improvement accounting for a problem that is easily solved by hand from time to time, so you may feel it's not worth the hassle

---

### Post by tgalati4 on 2014-09-22
I would replace *wget* and ftp with *rsync*.  That way you get a secure snapshot of your website.  With correct ssh key's, no password is needed.

There are lots of *rsync* scripts and tips on these forums.  ssh keys can be generated:  [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

I was not aware of the */2 syntax in cron.  I learned something new!  Run your script as is for a while and see what works and what doesn't.  That's part of the fun.

For *rsync*, there are a hundred ways to do it:  [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

[http://askubuntu.com/questions/20508/script-for-an-incremental-file-system-backup](http://askubuntu.com/questions/20508/script-for-an-incremental-file-system-backup)

---

### Post by chris137 on 2014-09-25
> **Vaphell said:**
> All in all it would be a minor improvement accounting for a problem that is easily solved by hand from time to time, so you may feel it's not worth the hassle
Well, exactly :D
Thanks though

@tgalati4
What would be the benefit of using rsynch over wget?

There were no problems yet, seems to be working.
Since there is a solution I'm marking this thread as solved.
Of course we still can discuss further improvements ;)

---

### Post by tgalati4 on 2014-09-25
Nothing is wrong with ftp on an internal, secured network.  But transfering across switches with other devices sniffing your packets, you may be concerned:

[http://rc.arizona.edu/hpc-htc/using-systems/transferring-files](http://rc.arizona.edu/hpc-htc/using-systems/transferring-files)

Really old, but short explaination of rsync:  [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

If the logic of your script works, then you can make small changes to it to improve security of the transfers.  It's not a problem.  Until it becomes a problem.

Every time your script executes, your password has the potential to be transmitted (in clear text) every two days.  If that password is the same password that controls your web server then you may be vulnerable.

From the *wget* manual page:

> FTP Options
       --ftp-user=user
       --ftp-password=password
           Specify the username user and password password on an FTP server.  Without this, or the corresponding startup option, the password defaults to
           -wget@, normally used for anonymous FTP.

           Another way to specify username and password is in the URL itself.  **Either method reveals your password** to anyone who bothers to run "ps".  To
           prevent the passwords from being seen, store them in .wgetrc or .netrc, and make sure to protect those files from other users with "chmod".
           If the passwords are really important, do not leave them lying in those files either---edit the files and delete them after Wget has started
           the download.


---

