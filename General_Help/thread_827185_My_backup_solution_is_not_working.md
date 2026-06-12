---
title: "My backup solution is not working"
date: 2008-06-12
forum: General Help
---

### Post by mashcaster on 2008-06-12
I've tried getting the following script to work but it does not.  Can someone please have a look at it and tell me what I am doing wrong?

#!/bin/sh

OPATH=/var/www/
LPATH=/home/mash/Desktop/backup
TPATH=/home/mash/Desktop/backup.tar
GPATH=/home/mash/Desktop/backup.gpg
MYKEY=mash@gmail.com

rdiff-backup $OPATH $LPATH
tar czf $TPATH $LPATH
rm $GPATH
gpg --output $GPATH --encrypt --recipient $MYKEY $TPATH
pftp ftp.drivehq.com <<END
cd /backup
delete backup.gpg
put backup.gpg
bye
END

---

### Post by mashcaster on 2008-06-16
Anyone? :confused:

---

### Post by bingoUV on 2008-06-16
What exactly do you mean when you say it does not work? 
1. Any errors reported? 
2. Does it take as long as you think it should take to rdiff-backup, then encrypt and then ftp all the stuff over? 
3. Does the data not reach the intended location?
4. Which part does not work?

---

### Post by aktiwers on 2008-06-16
Have you seen this? 
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

---

### Post by mashcaster on 2008-06-16
> **bingoUV said:**
> What exactly do you mean when you say it does not work? 
1. Any errors reported? 
2. Does it take as long as you think it should take to rdiff-backup, then encrypt and then ftp all the stuff over? 
3. Does the data not reach the intended location?
4. Which part does not work?

Basically, it create a file which is only a few bytes.  It should be creating a file which is a few kb.  When I type each line in the terminal individually, it works perfectly except i have to type sudo infront of the lines.

> **aktiwers said:**
> Have you seen this? 
[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

Checking it out right now.

edit, ok i have used that before, but back in the day it did not have the ability to automate backups with as much freedom as you get with cron to set specific or reoccurring times.

i don't know if the new version gives you as much freedom as cron?

---

### Post by Keith Hedger on 2008-06-16
Silly question but have u tried running the script as root, as u seem to need root perms when u run the commands from the command line?

---

### Post by bingoUV on 2008-06-16
> **mashcaster said:**
> Basically, it create a file which is only a few bytes.  It should be creating a file which is a few kb.  When I type each line in the terminal individually, it works perfectly except i have to type sudo infront of the lines.


How do you expect the script to know when to type sudo infont of the lines to make it work?

---

### Post by mashcaster on 2008-06-16
How do I run the script as root from crontab?

The strange thing is, it used to work until I added:
delete backup.gpg

---

### Post by bingoUV on 2008-06-16
You run it from root's crontab. Remove the entry from the user crontab, and add it in root's crontab. You can edit root's crontab by
```

sudo crontab -e

```

---

### Post by mashcaster on 2008-06-16
> **bingoUV said:**
> You run it from root's crontab. Remove the entry from the user crontab, and add it in root's crontab. You can edit root's crontab by
```

sudo crontab -e

```

I see!!!

I didn't realise that about crontab.

Ok, I will try that when I get home.

---

### Post by mashcaster on 2008-06-21
Still not working.  I finally got a chance to try this.

Here is my cron stuff, removed from the current user and added to root...

mash@ubuntu:~$ crontab -l
# m h  dom mon dow   command
mash@ubuntu:~$ sudo crontab -l
# m h  dom mon dow   command
00 * * * * /home/mash/Desktop/myscript.sh
mash@ubuntu:~$ 

Here is the script file

#!/bin/sh

OPATH=/var/www/
LPATH=/home/mash/Desktop/backup
TPATH=/home/mash/Desktop/backup.tar
GPATH=/home/mash/Desktop/backup.gpg
MYKEY=mash@gmail.com

rdiff-backup $OPATH $LPATH
tar czf $TPATH $LPATH
rm $GPATH
gpg --output $GPATH --encrypt --recipient $MYKEY $TPATH
pftp ftp.drivehq.com <<END
cd /backup
delete backup.gpg
put backup.gpg
bye
END

Do I need to give the myscript.sh some sort of rights?  It still produces a file on the ftp server which is only a few hundred bytes instead of a few hundred kb.

Please help.

---

### Post by mashcaster on 2008-06-21
I tried doing the whole thing manually, and unlike before, even the manual version will not work now...  Please help.

Here is the terminal output:

mash@ubuntu:~$ sudo rdiff-backup /var/www/ /home/mash/Desktop/backup
mash@ubuntu:~$ sudo tar czf /home/mash/Desktop/backup.tar /home/mash/Desktop/backup
tar: Removing leading `/' from member names
mash@ubuntu:~$ sudo rm /home/mash/Desktop/backup.gpg
rm: cannot remove `/home/mash/Desktop/backup.gpg': No such file or directory
mash@ubuntu:~$ sudo gpg --output /home/mash/Desktop/backup.gpg --encrypt --recipient [email]mash@gmail.com[/email] /home/mash/Desktop/backup.tar
gpg: WARNING: unsafe ownership on configuration file `/home/mash/.gnupg/gpg.conf'
mash@ubuntu:~$ sudo pftp ftp.drivehq.com
Connected to ftp.drivehq.com.
220 Welcome to the most popular FTP hosting service! Save on hardware, software, hosting and admin. Share files/folders with read-write permission. Visit [http://www.drivehq.com/ftp/](http://www.drivehq.com/ftp/)
331 User name ok, need password.
230 User successfully logged on.
Remote system type is UNIX.
ftp> cd /backup
250 CWD command successful. "/backup" is current directory.
ftp> delete backup.gpg
250 File "backup.gpg" was deleted successfully.
ftp> put backup.gpg
local: backup.gpg remote: backup.gpg
local: backup.gpg: No such file or directory
ftp> bye
220 Bye
mash@ubuntu:~$ 

I can see the backup.gpg file on the desktop but it has a little padlock on the top right corner.

---

### Post by mashcaster on 2008-06-23
Any idea?

---

### Post by mashcaster on 2008-06-24
Should I assume that the lack of replies is down to people not knowing the answer?

---

### Post by mashcaster on 2008-07-02
> **mashcaster said:**
> Should I assume that the lack of replies is down to people not knowing the answer?

Assumed.

---

