---
title: "Crontab entry not working"
date: 2018-08-14
forum: General Help
---

### Post by raleigh3 on 2018-08-14
I have this in my crontab.

@daily          root    /home/andy/bin/Backup_18_04.sh

As of 1:07 pm today, it still has not run. ?

The script does work.

---

### Post by TheFu on 2018-08-14
In a personal crontab, you cannot set the userid to run under. No userid allowed.  That would be a huge security hole, right?  In your example above, you added "root" - that is not allowed.  The templates didn't include  any mention of specifying any userid, did they?

There are a few options.
* root's crontab -  **sudo crontab -e** - this method uses the same format as I've help with in prior posts. There is no userid allowed.
* system crontab file - edit /etc/crontab and follow the existing examples for the format. I don't use this.
* the existing daily crontab directory in /etc/cron.daily/ ... just put the script into there, not any crontab-like entry. There should be a few example scripts already there. Follow them for user/group and permissions.

All scripts must setup any environment required.  It is NOT the same environment that a normal, end-user, login has. The PATH is shorter, no non-standard env vars are set.  Nothing is picked up from ~/.bashrc or any other config files in any HOME directory.

If you follow scripting best practices, these environment issues don't matter.  If you don't, then they might and probably will.

---

### Post by raleigh3 on 2018-08-14
I put script in cron.daily directory.

It still isn't running.

That's why I try to avoid crontab. 

It's a pain. Folks should not have to run thru hoops.

---

### Post by TheFu on 2018-08-14
> It still isn't running.
isn't very useful without any other data.

Did you set the permissions to be like the other scripts already there?

Did you set all environment variables that you need?  Any automation tool will require this. If you post the script, I can point out some issues, probably.  It hasn't "clicked" for you yet.  Once it does, you'll get it forever.

To compare environments, run sometime like /usr/bin/env > /tmp/cron-environment into a cron.daily script.  Compare that output with the output from /usr/bin/env run under your userid.  The differences are likely problems.  NEVER trust the PATH in a script.  Never assume HOME or ~/ are set.  NEVER assume the PWD is what you expect.  This is common across all scripts.

These aren't "hoops." There isn't any magic with running scripts or using cron.

---

### Post by raleigh3 on 2018-08-14
> **TheFu said:**
> isn't very useful without any other data.

Did you set the permissions to be like the other scripts already there?

Did you set all environment variables that you need?  Any automation tool will require this. If you post the script, I can point out some issues, probably.  It hasn't "clicked" for you yet.  Once it does, you'll get it forever.

To compare environments, run sometime like /usr/bin/env > /tmp/cron-environment into a cron.daily script.  Compare that output with the output from /usr/bin/env run under your userid.  The differences are likely problems.  NEVER trust the PATH in a script.  Never assume HOME or ~/ are set.  NEVER assume the PWD is what you expect.  This is common across all scripts.

These aren't "hoops." There isn't any magic with running scripts or using cron.

Permissions are the same. root

Here is the script.

```

Docs_Backups=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Documents_Backups/
Scripts_Backups=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Script_Backups/
# Backup Documents
gxmessage -fg red -font  'sans 30' -timeout 3  ' BACKING UP FILES FOR UBUNTU_MATE 18.04.3 LTS'
cd ~/Documents
zip -u -q Ubuntu_Documents.zip *.txt *.doc *.rtf *.html *.png *.pdf *.odt *.ods *.odg 
#rsync -av --update Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#cp Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Documents_`date +"%Y-%m-%d-%H-%M"`.zip                   # date is in year/month/day/hour/minute format
cp Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Documents_Backups/Ubuntu_Documents_`date +"%Y-%m-%d-%H-%M"`.zip 
cd /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Documents_Backups/
# This deletes those unneeded date files which are zero bytes
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#-------------------------------------------------------------------------------------------------------------
# Backup bookmarks file  
cd /home/andy/.mozilla/seamonkey/g4eiyedb.default/
#rsync -av --update bookmarks.html /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
cp -f places.sqlite /home/andy/.mozilla/firefox/u3c99cjo.default/
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#-------------------------------------------------------------------------------------------------------------
# Backup my Scripts
cd /home/andy/bin/
zip -u Ubuntu_Scripts.zip *.sh *.rb *.c *.py *.txt
#rsync -av --update Ubuntu_Scripts.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#cp Ubuntu_Scripts.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Scripts_`date +"%Y-%m-%d-%H-%M"`.zip
cp Ubuntu_Scripts.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Script_Backups/Ubuntu_Scripts_`date +"%Y-%m-%d-%H-%M"`.zip
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#-------------------------------------------------------------------------------------------------------------
# Backup sounds
cd /usr/share/sounds/My_Sounds/
echo yy | sudo -S zip -u My_Sounds.zip *.mp3 *.wav
rsync -av --update My_Sounds.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#-------------------------------------------------------------------------------------------------------------
# Backup icons
cd /home/andy/ICONS
zip -u -q Ubuntu_Icons.zip *.png *.pnm
rsync -av --update Ubuntu_Icons.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
find . -type f -size 0b -delete
sleep 1
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#------------------------------------------------------------------------------------------------------------
# Backup Desktop files i.e. .desktop files
cd /home/andy/Desktop/
zip -u -q  Desktop_Items.zip *.desktop
mv -u Desktop_Items.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#-------------------------------------------------------------------------------------------------------------
# Backup aliases
cd /home/andy/
zip -u .bash_aliases.zip .bash_aliases
rsync -av --update .bash_aliases.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#-------------------------------------------------------------------------------------------------------------
# Backup Thunar settings
cd /etc/xdg/Thunar/
echo yy | sudo -S zip -u Thunar_Settings.zip uca.xml
rsync -av --update Thunar_Settings.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
find . -type f -size 0b -delete
sleep 1
#-------------------------------------------------------------------------------------------------------------
# Backup reminder file for ReminderFox in Seamonkey
cp -u /home/andy/.mozilla/seamonkey/g4eiyedb.default/reminderfox/reminderfox.ics /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#-------------------------------------------------------------------------------------------------------------
# Make sure all files in SDB2 are owned by me
#echo yy | sudo -S chown -R andy /media/andy/MAXTOR_SDB2/
#-------------------------------------------------------------------------------------------------------------
# Backup my Custom panel layout
cd /usr/share/mate-panel/layouts/
echo yy | sudo rm My_Panel_Layout.zip
echo marlin | sudo -S zip -u My_Panel_Layout.zip Andys_Panel-tweak*.*
cp My_Panel_Layout.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
#-------------------------------------------------------------------------------------------------------------
# Create file with current date -- indicates when a backup was made
#
cd /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/
sleep 1
#
# This deletes those unneeded date files which are zero bytes
find . -type f -size 0b -delete
touch $( date '+%m-%d-%Y_%I:%M-%p' )
#
# Play a sound :-)
amixer -D pulse sset Master 40% > /dev/null 2>&1
cvlc --play-and-exit /home/andy/MY_SOUNDS/Tone.wav /dev/null 2>&1
gxmessage -fg green -font  'sans 30' -timeout 2 'BACKUP TO MAXTOR SDB1 COMPLETE. :-)'
amixer -D pulse sset Master 30% > /dev/null 2>&1

```

---

### Post by TheFu on 2018-08-14
> **raleigh3 said:**
> Permissions are the same. root

Here is the script.
<snip>


Permissions are
1) owner
2) group
3) 32-bit permissions 
4) any ACLs 
Permissions look like this in my world:
```
-rwxr-xr-x   1 root root   435 Nov 18  2014 mlocate*
``` I don't use ACLs very often.

**Script comments**
Some cron scripting ideas: [http://blog.jdpfu.com/2010/06/05/5-cron-tips](http://blog.jdpfu.com/2010/06/05/5-cron-tips)
General scripting ideas: [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

Don't trust the PATH.  All programs being called need a full path to their location.  It isn't env, needs to be /usr/bin/env instead.  ALL PROGRAMS need that. rsync, cp, find,  zip, mv ... all programs, especially when running as root. It is common to use environment vars for this stuff.
CP=/bin/cp   
then use $CP everywhere in the script.  Using the wrong version of all programs is a danger in a script.

gxmessage appears to be a GUI tool.  No GUI stuff allowed in cron, especially under a different userid like root.  GUI tools can only run under a currently logged in X/session using that same userid.  cron works the same today as it did  in 1971.  No GUI back then. No "desktop" back then.

All the stuff at the end to play a sound, etc.  shouldn't work either. Linux is multi-user. Only the currently logged in userid should have access to video or audio devices for output.  cron output is emailed to the userid (root in this case), so that should be checked daily. Send normal output to /dev/null and only send stderr to the email output from cron. You can also send the output to logs, if you like. Be certain to use a full path to the log files.

```
cd ~/Documents
```
Doesn't work in cron.  Best case, it will try to point to /root/Documents - but that probably doesn't exist.  Worst case, HOME isn't set which is used to complete the ~/ expansion.  Probably want to use /home/andy/Documents?

Be VERY careful using **find . -delete** in any script.  If a chdir command fails, the script will be in an unexpected directory and 'find' will search recursively below that other directory, then delete any files that match.  In a script, ALWAYS specify a full path for input into 'find' commands.

No need for sudo anywhere in a script that already runs under the root account.

You've done some good work with this script.  It is far beyond what my first backup script attempt was.  
I would use some convenience environment variables to make the script easier to follow and prevent typos from ruining things.  
SOURCE=/home/andy
TARGET=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04
DATE=$(/bin/date "+%F")
Then I'd use those everywhere inside the script instead of spelling it out.  Being consistent is good.

Whenever a script isn't working, simplify and test. Keep doing that until it does work. Simplify and test.

I'd also verify that the TARGET storage is the mount you expect.  I got burned by this once when storage wasn't available  due to a bad USB connection.  / got used and a full filesystem is a terrible thing.  I put a zero length file at the base of every mounted storage that I can test for existence.  If it isn't there, the storage isn't mounted and I exit.

If the TARGET storage isn't a Linux file system, then you will be losing permissions data.  Actually, I think ZIP loses permissions data too.  tar will keep user/group/Unix permissions, but tar is a poor backup tool.  There are many better choices.

What file system is the TARGET directory using?

That's the major stuff.

If you are interested, maybe using a backup tool that does the versioning and keeps permissions would be easier?

---

### Post by raleigh3 on 2018-08-15
Ok. I realize that's it's better to use crontab -e.

I have got my script running ok. Thanks for your help.

Have another issue when trying to send an email.

I put a script in crontab to send me an email when a backup script has completed.


  That script when run by itself does send me that email.

  
However, when it runs in crontab I get (from syslog)

  ```
Aug 15 03:49:02 7 CRON[5237]: (andy) CMD (/home/andy/bin/Send_Email.sh)
Aug 15 03:49:07 7 sSMTP[5241]: Creating SSL connection to host
Aug 15 03:49:07 7 sSMTP[5241]: SSL connection using ECDHE_RSA_AES_256_GCM_SHA384
Aug 15 03:49:07 7 cron[760]: sendmail: 450 Requested mail action not taken: mailbox unavailable
Aug 15 03:49:07 7 sSMTP[5241]: 450 Requested mail action not taken: mailbox unavailable
Aug 15 03:49:07 7 CRON[5236]: (andy) MAIL (mailed 63 bytes of output but got status 0x0001 from MTA#012)
Aug 15 03:49:46 7 gvfsd-metadata[1674]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed  This is the relavent part of crontab

```
     
Relevent part of my crontab

```
# m h  dom mon dow   command
   # Run my backup script at 10 a.m every day
   0 10 * * * /home/andy/bin/Backup_18_04.sh
  # Run my backup script at 8 p.m every day
  0 20 * * * /home/andy/bin/Backup_18_04.sh
  0 10 * * * /home/andy/bin/Send_Email.sh
  0 20 * * * /home/andy/bin/Send_Email.sh
  30 3 * * * /home/andy/bin/Send_Email.sh 
```

```
#!/bin/bash
# Ubuntu_Mate 18.04 LTS
#
# Send an email using a script
# Make sure there are several blank lines between Subject and the message.!!
CONTENT="Backup to Maxtor Drive has occured."
ssmtp -t << EOF
To: andrew_kennedy7@yahoo.com
From: andrew_kennedy7@yahoo.com
Subject: Backups to Maxtor Drive


$CONTENT
Cheers,
   Andy
EOF

```
 What is wrong?

---

### Post by raleigh3 on 2018-08-15
> **TheFu said:**
> Permissions are
1) owner
2) group
3) 32-bit permissions 
4) any ACLs 
Permissions look like this in my world:
```
-rwxr-xr-x   1 root root   435 Nov 18  2014 mlocate*
``` I don't use ACLs very often.

**Script comments**
Some cron scripting ideas: [http://blog.jdpfu.com/2010/06/05/5-cron-tips](http://blog.jdpfu.com/2010/06/05/5-cron-tips)
General scripting ideas: [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting)

Don't trust the PATH.  All programs being called need a full path to their location.  It isn't env, needs to be /usr/bin/env instead.  ALL PROGRAMS need that. rsync, cp, find,  zip, mv ... all programs, especially when running as root. It is common to use environment vars for this stuff.
CP=/bin/cp   
then use $CP everywhere in the script.  Using the wrong version of all programs is a danger in a script.

gxmessage appears to be a GUI tool.  No GUI stuff allowed in cron, especially under a different userid like root.  GUI tools can only run under a currently logged in X/session using that same userid.  cron works the same today as it did  in 1971.  No GUI back then. No "desktop" back then.

All the stuff at the end to play a sound, etc.  shouldn't work either. Linux is multi-user. Only the currently logged in userid should have access to video or audio devices for output.  cron output is emailed to the userid (root in this case), so that should be checked daily. Send normal output to /dev/null and only send stderr to the email output from cron. You can also send the output to logs, if you like. Be certain to use a full path to the log files.

```
cd ~/Documents
```
Doesn't work in cron.  Best case, it will try to point to /root/Documents - but that probably doesn't exist.  Worst case, HOME isn't set which is used to complete the ~/ expansion.  Probably want to use /home/andy/Documents?

Be VERY careful using **find . -delete** in any script.  If a chdir command fails, the script will be in an unexpected directory and 'find' will search recursively below that other directory, then delete any files that match.  In a script, ALWAYS specify a full path for input into 'find' commands.

No need for sudo anywhere in a script that already runs under the root account.

You've done some good work with this script.  It is far beyond what my first backup script attempt was.  
I would use some convenience environment variables to make the script easier to follow and prevent typos from ruining things.  
SOURCE=/home/andy
TARGET=/media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04
DATE=$(/bin/date "+%F")
Then I'd use those everywhere inside the script instead of spelling it out.  Being consistent is good.

Whenever a script isn't working, simplify and test. Keep doing that until it does work. Simplify and test.

I'd also verify that the TARGET storage is the mount you expect.  I got burned by this once when storage wasn't available  due to a bad USB connection.  / got used and a full filesystem is a terrible thing.  I put a zero length file at the base of every mounted storage that I can test for existence.  If it isn't there, the storage isn't mounted and I exit.

If the TARGET storage isn't a Linux file system, then you will be losing permissions data.  Actually, I think ZIP loses permissions data too.  tar will keep user/group/Unix permissions, but tar is a poor backup tool.  There are many better choices.

What file system is the TARGET directory using?

That's the major stuff.

If you are interested, maybe using a backup tool that does the versioning and keeps permissions would be easier?

Ok. Got rid of gxmessage, sound stuff, and use of ~.

My target backup drive is ext3.

I use deja-dup and Clonezilla.

Sometimes I get the dreaded Emergency mode and Clonezilla is the only thing that does a restore.

---

### Post by TheFu on 2018-08-15
If you see Grub emergency mode more than once, I'd swap out the HDDs, check all the cables, and change the ports (sata, esata, usb) used.  The system logs should have something about any storage failures that can be traced to a specific pipeline of controller, cable, disk.

I can't help with your email issues. I use postfix and run satellite email on all my systems, which is forwarded to the network email server for handling.

But ... there is no need to send email about cron jobs from a script run in cron. Cron is coupled to email already.  Every crontab entry sends output via email to the userid it runs under.  This is automatic, so trying to send email from a cron script is 100% redundant.

BTW, the script still isn't following the scripting best practices - **specify the full path to all programs.**

---

### Post by raleigh3 on 2018-08-15
Some of the emergency modes is from hitting the reset button on the computer when something was not responding.

---

### Post by #&amp;thj^% on 2018-08-15
> **raleigh3 said:**
> Some of the emergency modes is from hitting the reset button on the computer when something was not responding.

ssmtp perhaps.?

I forgot how to find path to program.

```
which -a sort # or your program here.
/usr/sbin/sort
/sbin/sort
/usr/bin/sort
/bin/sort


```
Forgot to add So if you have multiple versions, you can use the -a switch:
compared to:
```
which sort
/usr/sbin/sort

```

---

