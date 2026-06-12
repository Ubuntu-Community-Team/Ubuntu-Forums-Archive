---
title: "Automated backup of a folder"
date: 2013-02-12
forum: General Help
---

### Post by BigBubbaX on 2013-02-12
Hi,

I've recently installed Ubuntu Server 12.04.1 on an old laptop and set it up as a Minecraft server.

Between glitchy internet connections and griefing between my friends, I'm quite interested in setting up a hourly backups for the minecraft directory.

So far, I've made four .sh scripts in my first attempt to automate the backup.

I want to take the contents of the directory 'minecraft', create a .tar once a day, and place it in 'minecraft.backups'. 'minecraft.backups' has a subdirectory named 'hourly' that I'd like to keep 24 hourly .tars in. This way I'll always have a backup from the last 24 hours, and a daily backup for the last 7 days.

Both of my shell scripts are located in ~/minecraft.backups/

minecraft.dailybkup.sh:
```

bero@BBX-FloatServ:~/minecraft.backups$ more minecraft.dailybkup.sh
#
# MineCraft Auto Backup Service
# By: Christopher Bero [BigBubbaX]
#

#
# Set Up Script
#
# !/bin/bash
clear
echo "Minecraft Auto Backup Service initialized."

DAY=$(date +%d)
MONTH=$(date +%m)
YEAR=$(date +%Y)
ARCHIVE=$HOME/minecraft.backups/bkup.$YEAR.$MONTH.$DAY.tar
SERVER=$HOME/minecraft

#
# Perform Backup
#
tar -cf $ARCHIVE $SERVER
echo 'Backup Completed. Please check to ensure integrity.'
echo 'Archive: ' $ARCHIVE

#
# Check for Archives older than 14 days.
#
echo 'Checking for archives older than two weeks.'

rm `ls -t $HOME/minecraft.backups/*.tar | awk 'NR>14'`

#
# Check for Hourly Archives older than 24 hours.
#
echo 'Checking for hourly archives older than 24 hours.'

rm `ls -t $HOME/minecraft.backups/hourly/*.tar | awk 'NR>24'`

echo 'Ending Program.'

```

minecraft.hourlybkup.sh:
```
bero@BBX-FloatServ:~/minecraft.backups$ more minecraft.hourlybkup.sh
#
# MineCraft Auto Backup Service
# By: Christopher Bero [BigBubbaX]
#

#
# Set Up Script
#
# !/bin/bash
clear
echo "Minecraft Auto Backup Service initialized."

HOUR=$(date +%H)
DAY=$(date +%d)
MONTH=$(date +%m)
YEAR=$(date +%Y)
ARCHIVE=$HOME/minecraft.backups/hourly/bkup.$YEAR.$MONTH.$DAY.$HOUR.tar
SERVER=$HOME/minecraft

#
# Perform Backup
#
tar -cf $ARCHIVE $SERVER
echo 'Backup Completed. Please check to ensure integrity.'
echo 'Archive: ' $ARCHIVE

echo 'Ending Program.'

```


In /etc/cron.daily/ I have a file called minecraft.daily.caller.sh and mc.daily.out

minecraft.daily.caller.sh:
```
bero@BBX-FloatServ:/etc/cron.daily$ more minecraft.daily.caller.sh
#
# IDK yet
#
#

/home/bero/minecraft.backups/minecraft.dailybkup.sh > mc.daily.out

```

mc.daily.out is empty.

In /etc/cron.hourly/ I have a file called minecraft.hourly.caller.sh and mc.hourly.out

minecraft.hourly.caller.sh:
```
bero@BBX-FloatServ:/etc/cron.hourly$ more minecraft.hourly.caller.sh
#
# Untitled so far
#
#

/home/bero/minecraft.backups/minecraft.hourlybkup.sh > mc.hourly.out

```

mc.hourly.out is empty.

All of the above (non .out) files have +x enabled.

When I explicitly call a script, it runs.
```
bero@BBX-FloatServ:/etc/cron.hourly$ ./minecraft.hourly.caller.sh
tar: Removing leading `/' from member names
bero@BBX-FloatServ:/etc/cron.hourly$ more mc.hourly.out
Minecraft Auto Backup Service initialized.
Backup Completed. Please check to ensure integrity.
Archive:  /home/bero/minecraft.backups/hourly/bkup.2013.02.12.13.tar
Ending Program.

```

But neither of the scripts have run of their own accord yet, after over a day of me tinkering on and off.

I'd appreciate any pointers someone is willing to give me.

Thanks!,
BBX

---

### Post by BigBubbaX on 2013-02-12
Directories:

My home directory:
```
bero@BBX-FloatServ:~$ ls -last
total 60
4 drwxr-xr-x 7 bero bero 4096 Feb 11 22:33 .
8 -rw------- 1 root root 6433 Feb 11 22:33 .viminfo
4 drwxrwxr-x 3 bero bero 4096 Feb 11 22:30 minecraft.backups
4 drwxrwxr-x 4 bero bero 4096 Feb 11 22:21 minecraft
8 -rw------- 1 bero bero 6505 Feb 11 20:55 .bash_history
4 drwxrwxr-x 2 bero bero 4096 Feb 11 14:35 logs
4 -rw------- 1 bero bero   59 Feb 11 14:23 .Xauthority
4 drwx------ 2 bero bero 4096 Feb  7 13:50 .ssh
4 drwx------ 2 bero bero 4096 Feb  7 11:45 .cache
4 drwxr-xr-x 3 root root 4096 Feb  7 11:43 ..
4 -rw-r--r-- 1 bero bero  220 Feb  7 11:43 .bash_logout
4 -rw-r--r-- 1 bero bero 3486 Feb  7 11:43 .bashrc
4 -rw-r--r-- 1 bero bero  675 Feb  7 11:43 .profile

```

minecraft.backups:
```
bero@BBX-FloatServ:~/minecraft.backups$ ls -last
total 328832
     4 drwxr-xr-x 2 bero bero      4096 Feb 12 13:54 hourly
111792 -rw-rw-r-- 1 bero bero 114472960 Feb 12 13:48 bkup.2013.02.12.tar
     4 drwxrwxr-x 3 bero bero      4096 Feb 12 13:48 .
     4 drwxr-xr-x 7 bero bero      4096 Feb 11 22:33 ..
     4 -rwxrwxrwx 1 bero root       485 Feb 11 13:32 minecraft.hourlybkup.sh
     4 -rwxrwxrwx 1 root root       782 Feb 11 13:26 minecraft.dailybkup.sh
108640 -rw-rw-r-- 1 bero bero 111247360 Feb 11 00:51 bkup.2013.02.11.tar
108380 -rw-rw-r-- 1 bero bero 110981120 Feb 10 02:34 bkup.2013.02.10.tar

```

hourly:
```
bero@BBX-FloatServ:~/minecraft.backups/hourly$ ls -last
total 333032
111792 -rw-rw-r-- 1 bero bero 114472960 Feb 12 13:54 bkup.2013.02.12.13.tar
     4 drwxr-xr-x 2 bero bero      4096 Feb 12 13:54 .
     4 drwxrwxr-x 3 bero bero      4096 Feb 12 13:48 ..
111780 -rw-rw-r-- 1 bero bero 114462720 Feb 11 22:29 bkup.2013.02.11.22.tar
109452 -rw-rw-r-- 1 bero bero 112076800 Feb 11 14:27 bkup.2013.02.11.14.tar

```

cron.daily:
```
bero@BBX-FloatServ:/etc/cron.daily$ ls -last
total 84
 4 drwxr-xr-x   2 root root  4096 Feb 11 22:33 .
 0 -rwxrwxrwx   1 root root     0 Feb 11 22:33 mc.daily.out
 4 -rwxrwxrwx   1 root root    86 Feb 11 22:33 minecraft.daily.caller.sh

```

cron.hourly:
```
bero@BBX-FloatServ:/etc/cron.hourly$ ls -last
total 20
4 -rwxrwxrwx   1 root root  187 Feb 12 13:54 mc.hourly.out
4 drwxr-xr-x   2 root root 4096 Feb 11 22:29 .
4 -rwxrwxrwx   1 root root   97 Feb 11 22:29 minecraft.hourly.caller.sh
4 drwxr-xr-x 112 root root 4096 Feb 11 00:55 ..
4 -rw-r--r--   1 root root  102 Apr  2  2012 .placeholder

```

The .tars that do exist are when I have called the shell scripts explicitly.

Thanks!,
BBX

---

### Post by Cheesemill on 2013-02-12
If the backup scripts are being run by root then your ARCHIVE and SERVER variables are going to pointing to the wrong place, /root instead of /home/bero.

Try using 'crontab -e' to add the scripts to your user crontab instead of roots.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Take a look in the /root directory and see if your backups have been created there.

---

### Post by BigBubbaX on 2013-02-12
Cheesemill,
I've implemented your suggestion, and it appears to be working. Thank you for pointing me in the right direction!

Thanks,
BBX

---

