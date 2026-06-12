---
title: "Need rsync back up script"
date: 2013-02-04
forum: General Help
---

### Post by minicomish on 2013-02-04
Hello There, I have two servers running Ubuntu 12.10. One is a back up server an the other is the main server where my website is hosted. I need a script that back's up the whole of the main server and mysql as it is a Wordpress blog to /home/user/backup on the back up server. it needs to use rsync an connect using ssh keys an also need's to be automatic every 30 min's using cron, Thanks minicomish.

---

### Post by elliotn on 2013-02-04
me too

---

### Post by papibe on 2013-02-05
Hi minicomish. Welcome to the forums!

Is very difficult to offer specifics because you don't explain many details.

Here are a few tips:
[LIST]
[*]Install openssh-server on the backup server.
[*]Set up a passwordless keys (read [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")).
[*]rsync your files, but do not rsync your MySQL database.
[*]Use internal MySQL replication to make copies of your database to the backup server.
[/LIST]
That should get you started. Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2013-02-05
I'll add using mysqldump to create a plain-text backup of the database before running rsync.

---

### Post by rnerwein on 2013-02-06
> **papibe said:**
> Hi minicomish. Welcome to the forums!

Is very difficult to offer specifics because you don't explain many details.

Here are a few tips:
[LIST]
[*]Install openssh-server on the backup server.
[*]Set up a passwordless keys (read [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")).
[*]rsync your files, but do not rsync your MySQL database.
[*]Use internal MySQL replication to make copies of your database to the backup server.
[/LIST]
That should get you started. Let us know how it goes.
Regards.
hi
i run this script years ago on solaris. but in ubuntu it don't work. (never change a running system).
#-----------------------------------------------------------------#
# agent is started on fist login once - or you'r remote
# this agent is valid for all your primary login screens
# make shure that your profile (eg. .profile, .ksh or .dterm will
# be executed at login time - if not -> you are a loser :-((
#-----------------------------------------------------------------#
#
# sometimes the shortest way is to take the negative way

if [ ! `ps -u $LOGNAME | grep -c ssh-agent` ]
then
    if [ -z "$SSH_CLIENT" ]
    then
        ssh-add </dev/null >/dev/null 2>&1
        r_c=$?
        [ $r_c -ne 0 ] && eval $(ssh-agent)
    fi
fi

# the agent will be killed if the session is finished - logout
trap "kill $SSH_AGENT_PID >/dev/null 2>&1" 0

i am every time (first time only) asked for my password. and even the unix default trap 0 (it's on the beginning of my .profile and .bashrc - i tried both - get no trap ?!)
if ubuntu got a new feature - please tell me. 
it hassle me much - because i know !
cheers

---

### Post by minicomish on 2013-02-06
Thanks for the replies everyone. I just need a basic rsync script to back my server up to a remote location an backup mysql, Ive looked all over the interwebs but there isn't a complete solution as im new to backing up using rsync but have been using ubuntu for about 5 years an i love it, Thanks minicomish.

---

### Post by rewyllys on 2013-02-06
My suggestion is that you install LuckyBackup.  

It provides a well designed GUI that makes it easy to select the folders that you want to backup and the target where you want to store the backed-up folders and their files.  Also, LuckyBackup makes it easy to schedule your backups.

I've used it for several years without any problems.

---

### Post by oldfred on 2013-02-06
Some general info:

       Rsync & Backup With Rsync and Ssh
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
 [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

    Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

    Some folders to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

    More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

       Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

            rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by minicomish on 2013-02-06
Thanks for that, shall take a look :)

---

