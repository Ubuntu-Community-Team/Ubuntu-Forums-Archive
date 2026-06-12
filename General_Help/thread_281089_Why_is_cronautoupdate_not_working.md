---
title: "Why is cron/autoupdate not working?"
date: 2006-10-20
forum: General Help
---

### Post by helpdeskdan on 2006-10-20
I don't get it... it should work, why isn't my system autoupdating at midnight?!

root@dave-desktop:/home/dan# crontab -e

0 0 * * * aptitude -y update && aptitude -y upgrade && aptitude -y dist-upgrade && aptitude -y autoclean

---

### Post by dannyboy79 on 2006-10-20
i am a newbie but recently looked into auto updating my system as well. I am pretty sure it's not working because you're using YOUR cron file and you can't perform update or upgrade etc etc without using sudo. You need to switch user to root, I think. there is also a program called apt-get cron, I think or maybe it's cron apt-get. which does all this for you. also, there are other's in this forum discussing this as well. doa search for auto update using cron.

---

### Post by helpdeskdan on 2006-10-20
Thank you kindly for your reply!  If you look at the output, you will note I was editing the crontab as root.  I set it last night but, when I checked today, it had not updated.  Doesn't make sense.

---

### Post by dcstar on 2006-10-20
> **helpdeskdan said:**
> Thank you kindly for your reply!  If you look at the output, you will note I was editing the crontab as root.  I set it last night but, when I checked today, it had not updated.  Doesn't make sense.

AFAIK cron jobs do not run in shells that have the paths set, so the cron job has no idea where the "aptitude" binary is.

Put the whole path in front of the command and see if things change.

---

### Post by helpdeskdan on 2006-10-21
Good idea!  Hadn't thought of that.  Didn't work, but still a good idea!
root@dave-desktop:/home/dan# ps ax | grep cron
 4367 ?        Ss     0:00 /usr/sbin/cron

I don't get it - it should work.

---

### Post by dcstar on 2006-10-21
> **helpdeskdan said:**
> Good idea!  Hadn't thought of that.  Didn't work, but still a good idea!
root@dave-desktop:/home/dan# ps ax | grep cron
 4367 ?        Ss     0:00 /usr/sbin/cron

I don't get it - it should work.

On review I do not think your line can work in cron - it is full of shell commands (the "&&") and cron knows nothing of any of that.

Put the whole command string into a separate executable shell file (look at others in your system for examples) and then have cron run that file.

---

### Post by helpdeskdan on 2006-10-21
That works, many thanks.  To document for future readers.  (Note - when editing crontab I was root and I set the time for midnight.  Optionally, install beep and uncomment line to get a happy little computer beep when your computer update) 

dan@ubuntu:~$ cat autoupdate
#/bin/sh
#beep -f 1000 -n -f 2000 -n -f 1500
aptitude -y update && aptitude -y upgrade && aptitude -y dist-upgrade && aptitude -y autoclean


root@ubuntu:/home/dan# chmod 777 autoupdate
root@ubuntu:/home/dan# crontab -e

# m h  dom mon dow   command
0 0 * * * /home/dan/autoupdate

Not so hard!  Thanks all!

---

### Post by helpdeskdan on 2006-10-22
Huh... that's odd.  Spoke too early.  Just tried it on another machine and it didn't quite work right.  It RAN, but didn't finish or something.

root@dave-desktop:/home/dan# ps ax
...
15006 ?        S      0:00 /USR/SBIN/CRON
15007 ?        Ss     0:00 /bin/sh -c /home/dan/autoupdate
15008 ?        Sl     0:05 aptitude -y update
...

root@dave-desktop:/home/dan# ps ax
...
15006 ?        S      0:00 /USR/SBIN/CRON
15007 ?        Ss     0:00 /bin/sh -c /home/dan/autoupdate
...
15023 ?        Sl     0:06 aptitude -y upgrade
...

Didn't seem to get any further nor did it finish the upgrade.  Maybe it was killed too early?

---

### Post by helpdeskdan on 2006-11-26
Ok, I got it.  To document for others the solution is to add a path.

#/bin/sh
PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
aptitude -y update && aptitude -y upgrade && aptitude -y dist-upgrade && aptitude -y autoclean

Just did an 'echo $PATH' & copy and pasted.  This appears to work correctly now.

---

### Post by dpgraves on 2007-03-05
Have written a script to autoupdate that notifies via email what updates have been done 

Have 1 question if anyone can answer it in the subject of the email like to be able to include the date of the updates eg  Subject "Update on 05/03/2007" or similar format, I have numerous machines and tried to give as much details as possible so anyone else can try this out 
Full instructions in this file 

#!/bin/sh
# Need to install three program prior to running in cron
# sudo aptitude install sendEmail beep
# sudo aptitude install postfix
# no Configuration as option postfix file
# The name in ****name*** refers to your home directory of sudo user
# There files to be created autoupdate, autoupdate.log, autoupdate.blank.log
# this file called autoupdate
# run sudo aptitude update and make sure no errors when run eg need new keys etc

LOG=/home/***name***/autoupdate.log
PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

cp /home/***name***/autoupdate.logbk4 /home/***name***/autoupdate.logbk5
cp /home/***name***/autoupdate.logbk3 /home/***name***/autoupdate.logbk4
cp /home/***name***/autoupdate.logbk2 /home/***name***/autoupdate.logbk3
cp /home/***name***/autoupdate.logbk1 /home/***name***/autoupdate.logbk2
cp /home/***name***/autoupdate.log /home/***name***/autoupdate.logbk1
cp /home/***name***/autoupdate.blank.log /home/***name***/autoupdate.log

echo "*******************************************************">>$LOG
echo "*                                                     *">>$LOG
echo "*   Running updates on `date`   *" >> $LOG
echo "*                                                     *">>$LOG
echo "*******************************************************" >> $LOG
# Just to let you know that script is running
beep -f 1000 -n -f 2000 -n -f 1500 
# not logged into the autoupdate.log to log info use 
# /usr/bin/aptitude -y update >> /home/***name***/autoupdate.log 2>&1
/usr/bin/aptitude -y update 
/usr/bin/aptitude -y upgrade >> /home/***name***/autoupdate.log 2>&1
#Comment out dist-upgrade if do not unsave updates eg kernels 
/usr/bin/aptitude -y dist-upgrade >> /home/***name***/autoupdate.log 2>&1
/usr/bin/aptitude -y autoclean >> /home/***name***/autoupdate.log 2>&1
# second beep to let you know update completed
beep -f 1000 -n -f 2000 -n -f 1500
#  -f send from a computer name used if more than one computer will be updated eg identify each machine
# -u just subject for updates
# -t sends emails to email address specified 

cat /home/***name***/autoupdate.log | sendEmail -f ***computername***@***domain***.com -u updates -t ***name***@***domain***.com
# this file is to be called "autoupdate"
# create two blank files one called "autoupdate.log" second "autoupdate.blank.log"
# the other files will create automatically to keep 5 previous updates if email not working etc
# need to make sure autoupdate.log and autoupdate.blank.log is available to all users.
# eg sudo chmod 777 autoupdate.log 
# and sudo chmod 777 autoupdate.blank.log
# then at home directory of a sudo user 
# sudo crontab -e

# uncomment top line if want to run everyday or bottom line if once per week etc
# m h  dom mon dow   command
# 30 19 * * *  /home/***home***/autoupdate
# minutes Hours every day

# 30 19 * * fri /home/***home***/autoupdate
# use to only run on one set day of week

# 30 19 * * mon,fri /home/***home***/autoupdate
# use to run twice a week on set days


Let me know if anyone can help with email date in subject field

Newbie to Linux but loving everyday of my none Microsoft life.

---

