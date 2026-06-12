---
title: "Shell script via crontab problem"
date: 2007-01-14
forum: General Help
---

### Post by yoshtodd on 2007-01-14
I'm trying to run a shell script that will do automatic backups. When I run it manually everything is fine so I'm assuming the script itself is okay. However I can't seem to get crontab to run it. I made an entry using sudo crontab -e (Script needs to be run as root) and here's the output from sudo crontab -l:

$ sudo crontab -l
30 * * * * /home/yoshtodd/Desktop/backup


Shell script named backup is on my desktop for now. Been checking when the clock hits 30 and nothing... any ideas what I'm doing wrong? Thanks in advance.

---

### Post by ardchoille42 on 2007-01-14
> **yoshtodd said:**
> I'm trying to run a shell script that will do automatic backups. When I run it manually everything is fine so I'm assuming the script itself is okay. However I can't seem to get crontab to run it. I made an entry using sudo crontab -e (Script needs to be run as root) and here's the output from sudo crontab -l:

$ sudo crontab -l
30 * * * * /home/yoshtodd/Desktop/backup


Shell script named backup is on my desktop for now. Been checking when the clock hits 30 and nothing... any ideas what I'm doing wrong? Thanks in advance.

I would suggest changing your crontab entry to this:

30 * * * * sh /home/yoshtodd/Desktop/backup

---

### Post by yoshtodd on 2007-01-15
Didn't work this time... will try and leave it on overnight I guess. Appreciate the fast response though.

---

### Post by keithweddell on 2007-01-15
You're probably going to need to post some details of your script.  But for starters, you may need to set the PATH variable in the script.

Keith

---

### Post by yoshtodd on 2007-01-15
Okay here's the script in it's entirety it's not too long:

```
#!/bin/bash
# This batch file backs up the data from SHARE
# -------------SCRIPT VARIABLES---------------
SHARE="(my shared drive)";
DATADIR="test";              
BACKUPFILE="test";
BACKUPDRIVE="/dev/hdc1";
BACKUPMP="/home/yoshtodd/";
SMBMP="/mnt/smb/";
# ---------------------------------------------
export PASSWD;
echo 'go';
smbumount $SMBMP;
smbmount $SHARE $SMBMP;
if (ls $SMBMP) then
     echo "Backing up $SHARE";
     cd $BACKUPMP;
     zip -r -u -v $BACKUPFILE $SMBMP;
     cd /;
fi;
smbumount $SMBMP;
```


It's a slightly altered version of one in a guide I followed found at [http://www.linuxjournal.com/article/4360](http://www.linuxjournal.com/article/4360).

The script itself does what it's supposed to when I run it from the terminal. Do you mean put a path variable in the script itself or in the crontab script? What would the path variable be in this case?

Also here's my crontab -l output now, I tried putting a copy of the shell script in /usr/bin as well but still no luck.
```
# m h  dom mon dow   command
59 * * * * sh /home/yoshtodd/Desktop/backup
30 * * * * sh /usr/bin/backup
```

---

### Post by keithweddell on 2007-01-15
OK.  I'm not an expert on these things but I have had similar problems in the past.  I know you should be able to run it from your home directory.  I think it's because cron doesn't know the path variable.  So try putting in a line near the top of your script as follows:

PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin


Keith

---

### Post by yoshtodd on 2007-01-15
Okay I put it in but now there's a new problem. After restarting both computers this morning the folder "test" no longer shows up on the shared network. I made sure it was still shared on the Windows machine and tried restarting samba on this one and nothing. Don't know why this would happen after just restarting, getting frustrated :/.

---

### Post by yoshtodd on 2007-01-15
All right ignore previous entry a nice person in #ubuntu on irc helped me access my folder again :). I added PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin to the shell script and it's still not running for some reason... Anyone know what I need to do?

---

### Post by thomasaaron on 2007-01-16
If you have to run the script as sudo, I'm guessing it requires you to enter a password.
If you are running it from crontab, you'll not get the opportunity to put in the password. Right?

I've not had any luck on getting crontab to open a gui application like gnome-terminal. But if you can figure out how to do that, you can open the terminal gui and run your script in it. It will prompt for a password, which you will have to enter, and voila.

---

### Post by keithweddell on 2007-01-16
Ah - didn't spot that you were running this from your own crontab.  Try running it from root's crontab by putting a copy in /etc/cron.hourly.  (I think you can also do this by symlink from /etc/cron.hourly to your script).

Keith

PS check out zenity if you want a pop up box.

---

### Post by yoshtodd on 2007-01-16
> **keithweddell said:**
> Ah - didn't spot that you were running this from your own crontab.  Try running it from root's crontab by putting a copy in /etc/cron.hourly.  (I think you can also do this by symlink from /etc/cron.hourly to your script).

Keith

PS check out zenity if you want a pop up box.

Okay I put a copy of the script in /etc/cron.hourly ... will leave it on overnight and see if it works.

---

### Post by yoshtodd on 2007-01-16
> **thomasaaron said:**
> If you have to run the script as sudo, I'm guessing it requires you to enter a password.
If you are running it from crontab, you'll not get the opportunity to put in the password. Right?.


Someone told me that if you sudo crontab -e, then the script would run with root privledges and not prompt for password.

---

### Post by yoshtodd on 2007-01-16
Well I'm about to give up... putting it in /etc/cron.hourly didn't work... I tried putting entries in /etc/crontab like a website suggested and no luck. Don't know what else to try.

---

### Post by walmartshopper67 on 2007-01-16
Yeah, i'm having the same problem - NOTHING runs in cron, either in the folders (etc/cron.whatever) or from the crontab entries. I know the scripts and the crontab entries work - i've tested them on another machine. Something goofy with cron in edgy?

---

### Post by yoshtodd on 2007-01-16
> **walmartshopper67 said:**
> Yeah, i'm having the same problem - NOTHING runs in cron, either in the folders (etc/cron.whatever) or from the crontab entries. I know the scripts and the crontab entries work - i've tested them on another machine. Something goofy with cron in edgy?

Hey I finally got mine to work with the help of some patient people in #ubuntu on irc :D ... Try using sudo crontab -e. Put your entry in then make sure there are a couple blank lines below it (hit enter a few times). If it still doesn't work try putting "> /home/yourusername/logfile" after your crontab command and see what's inputted into logfile. Also try System>Administration>System Log... look at the syslog and see if crontab is running when you specify or not.

---

