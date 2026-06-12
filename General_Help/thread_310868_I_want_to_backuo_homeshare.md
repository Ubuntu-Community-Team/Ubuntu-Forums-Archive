---
title: "I want to backuo /home/share"
date: 2006-12-01
forum: General Help
---

### Post by CameronCalver on 2006-12-01
Hello i have a share drive that shares to 7 computers with the use of samba and i would like to back that up every monday and every wednesday to /media/usbdisk.
I have tryed simple backup it was good becuase i could exclude files but when i clicked backup it did not do anything.
Does anyone no of any good programs that will do this

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> Hello i have a share drive that shares to 7 computers with the use of samba and i would like to back that up every monday and every wednesday to /media/usbdisk.
I have tryed simple backup it was good becuase i could exclude files but when i clicked backup it did not do anything.
Does anyone no of any good programs that will do thisI use cron for exactly what you need to do. Info on cron is [here]("http://en.wikipedia.org/wiki/Cron"). To access your cron file, use```
crontab -e
```. For example, my crontab file looks like this:```
0 * * * * /usr/bin/rsync -a --delete /home/gerb/ /mnt/backup/home/gerb/
15 * * * * /usr/bin/rsync -a --delete /mnt/storage/ /mnt/backup/storage/
```The first command runs every hour at the top of the hour and backs up my home directory to another drive at /mnt/backup/... . The second command runs every hour at minute 15 and backs up something else. You could change the schedule to fit your needs (explained in the linked document).

---

### Post by CameronCalver on 2006-12-02
ok i dont really get that what would i do if i want it to backup /home/server/share onto /media/usbdisk at 3:30 monday and friday and name the file backup_thedate

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> ok i dont really get that what would i do if i want it to backup /home/server/share onto /media/usbdisk at 3:30 monday and friday and name the file backup_thedateHere's your command:```
30 3 * * 1,5 /usr/bin/rsync -a --delete /home/server/share/ /media/usbdisk/share$(/bin/date +\%Y\%m\%d)
```You should first copy/paste the command (everything after the "5") into the terminal to make sure it does what you want it to do. Then add it to your crontab.

---

### Post by CameronCalver on 2006-12-02
Wont that do it on monday and friday so did u mean 1,3 and what does that -a -delete command do and also can i make it zip the file?

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> Wont that do it on monday and friday so did u mean 1,3 and what does that -a -delete command do and also can i make it zip the file?Yes, that will do it on Monday and Friday...that's what you said you wanted. Also, times are military time, so 3:30 is 3:30am. As for the zip file, you could use the following instead of the rsync command in your crontab:

/bin/tar -czf /your/backup/location/home.tar.gz$(date +\%Y\%m%d) /home/<user>

You'll need write access to wherever you want to save the .tar.gz file.

---

### Post by CameronCalver on 2006-12-02
Its came up with
```
cameron@ubuntu:~$ /bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk
/bin/tar: Removing leading `/' from member names

```
and also is there away i can make it so once there is 10 archives it deletes 7

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> Its came up with
```
cameron@ubuntu:~$ /bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk
/bin/tar: Removing leading `/' from member names

```
and also is there away i can make it so once there is 10 archives it deletes 7I don't think there's a simple way to do it, but I'm pretty sure you could write a shell script to do what you want. I'm not a script person, though.

---

### Post by CameronCalver on 2006-12-02
and can i change it from tar.gz to rar? and any script people here can  u help me out

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> and can i change it from tar.gz to rar? and any script people here can  u help me outSure, use "rar" instead of "tar"...parameters will be different, of course. Read:```
man rar
```

---

### Post by CameronCalver on 2006-12-02
I did this

```
cameron@ubuntu:~$ /bin/rar /home/cameron/share.rar$(date +\%Y\%m%d) /media/usbdisk

```
but it said /bin/rar no file or dir but then i tried 
cameron@ubuntu:~$rar -a -ap /home/cameron/share.rar$(date +\%Y\%m%d) /media/usbdisk and it didnt work -a means add files to archive and -ap means addy date to file name but i dont get all the options can you tell me how to just make a file share.thedate.rar in /media/usbdisk

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> I did this

```
cameron@ubuntu:~$ /bin/rar /home/cameron/share.rar$(date +\%Y\%m%d) /media/usbdisk

```
but it said /bin/rar no file or dir but then i tried 
cameron@ubuntu:~$rar -a -ap /home/cameron/share.rar$(date +\%Y\%m%d) /media/usbdisk and it didnt work -a means add files to archive and -ap means addy date to file name but i dont get all the options can you tell me how to just make a file share.thedate.rar in /media/usbdiskI think rar is at /usr/bin/rar, but I'm not familiar with the options. Why not use tar? There is a version of tar for Windows [here]("http://gnuwin32.sourceforge.net/packages/tar.htm") if you're worried about being able to decompress files in Windows.

---

### Post by CameronCalver on 2006-12-02
Thankyou so much i didnt no there was a tarball program for windows so now i need to try and make it delete files older then 2 weeks and when i do
bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk it says  /bin/tar: Removing leading `/' from member names
 what does this meen

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> Thankyou so much i didnt no there was a tarball program for windows so now i need to try and make it delete files older then 2 weeks and when i do
bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk it says  /bin/tar: Removing leading `/' from member names
 what does this meenI think it is referring to files in /media/usbdisk, for example, /media/usbdisk/somefile.txt. Instead of storing the file name as "/media/usbdisk/somefile.txt" it stores it as "media/usbdisk/somefile.txt". Just a guess.

---

### Post by CameronCalver on 2006-12-02
So what do i do to fix it

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> So what do i do to fix itThere's nothing to fix - it shouldn't matter.

---

### Post by CameronCalver on 2006-12-02
yep worked fine thanx

---

### Post by gerbman on 2006-12-02
> **CameronCalver said:**
> yep worked fine thanxWelcome.

---

### Post by CameronCalver on 2006-12-02
And just another thing i have 2 computers at home and a fileserver networked with ssh with a 80gb hd on is there a way i can everyweek make a file called backup_cam then the date and another one from a different location that saves as backup_calver then the date but every week it deletes the old one then adds the new one?

---

### Post by CameronCalver on 2006-12-22
hello i tryed making a launcher from the desktop i put name as backup command
bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk 
and run in terminal but it made the file as share.tar.gz(date not the actual date

---

### Post by gerbman on 2006-12-23
> **CameronCalver said:**
> hello i tryed making a launcher from the desktop i put name as backup command
bin/tar -czf /home/cameron/share.tar.gz$(date +\%Y\%m%d) /media/usbdisk 
and run in terminal but it made the file as share.tar.gz(date not the actual dateIn the launcher setup window, is there an option to run the command in a terminal? If so, use it. If there isn't such an option, then the command might not work. I'm on a Windows machine right now, so I can't confirm this. BTW - what is the actual filename that gets created?

---

### Post by CameronCalver on 2006-12-23
i did click run in terminal and it said 
```
backup.tar.gz$(date
```

---

### Post by CameronCalver on 2006-12-26
does anyone no the solution to this problem

---

### Post by gerbman on 2006-12-26
> **CameronCalver said:**
> does anyone no the solution to this problemYou could put the command in a shell script and call that script from the launcher. The script would look something like this:```
#!/bin/bash

<your command here>

```
Save it in a file (e.g., backup.sh), give it execute permissions:```
chmod +x backup.sh
```then give the path to the script for the launcher command.

---

