---
title: "I missed up my Ubuntu"
date: 2008-07-05
forum: General Help
---

### Post by snkngshps on 2008-07-05
I was following [this guide]("http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml") and somewhere along the line I have messed up Ubuntu. When I did a restart I was brought to a blue screen with a grey box that says..

"Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display wil be
disabled. Please restart the GDM when
the problem is corrected."

Unfortuantely I don't know how to check the syslog or even what to do if I could find it. Can anyone help?

---

### Post by werries on 2008-07-05
the bit where they edited the /etc/fstab is what screwed it up.(After reading comments below).

You need to revert to the old one. You could use a livecd to access the partition if you cannot access your system, or use recovery mode(if you know what you're doing with a terminal text editor)

---

### Post by snkngshps on 2008-07-05
That's the part I thought messed up :-/

I'm trying to find my live cd now but is there a way to edit this file from the shell? I can get to the shell at the start up but if I try a regular "sudo gedit /etc/fstab" it doesn't work (since that normally opens in a new window). Is there any other way to edit this from the shell?

---

### Post by FlyingWV on 2008-07-05
From the shell you can just do a sudo nano /etc/fstab and edit it that way from within the shell. I'm pretty sure. Or whichever editor you prefer/have installed. But nano should be installed.

---

### Post by werries on 2008-07-05
i don't know how to, but shouldnt he know the shortcuts for saving, at least?

---

### Post by Elfy on 2008-07-05
use nano - sudo nano filepath

Ctrl+O and enter to save 
Ctrl+X to exit

If you do it from recovery mode then you won't need sudo as it is root, it might be worth checking for a backu, gedit makes one with ~as part of filename

```
sudo mv /etc/fstab~ /etc/fstab
```

will overwqrite fstab with backup

---

### Post by FlyingWV on 2008-07-05
Like Forestpixie said, ctrl + x will exit... If you've made changes it'll prompt you to save that way as well, if you don't feel like ctrl + o :)

Good luck

---

### Post by lukjad on 2008-07-05
> **snkngshps said:**
> That's the part I thought messed up :-/


I'm trying to find my live cd now but is there a way to edit this file from the shell? I can get to the shell at the start up but if I try a regular "sudo gedit /etc/fstab" it doesn't work (since that normally opens in a new window). Is there any other way to edit this from the shell?

________________________
Edit
Awww man! I really got to brush up on my typing skills. **forestpixie** I will be avenged! (Nice post BTW.)
________________________

Type THIS:
```
cd /etc/
```
Then:
```
ls -h
```
Then look for the ***_fstab~_*** and the type:
```
sudo nano fstab~
```
When in nano hit the Ctrl+o key and when prompted for a name erase the ~ and say yes to overwrite. Then restart your PC and all will be well.

---

### Post by Elfy on 2008-07-05
yes I know about that - because I'm cynical - if it should and it doesn't and I've said do that - it's my fault :D

All that said if op used gedit then there should be a backup to use

@snkngshps - in future might be worth making backups as you go, syntax is

```
sudo cp /path/to/filename /path/to/filename.bak
``` or whatever you might like to put on the end - I use dates as a matter of course.


> When in nano hit the Ctrl+o key and when prompted for a name erase the ~ and say yes to overwrite. Then restart your PC and all will be well.surely it's easier to just mv the file

---

### Post by snkngshps on 2008-07-05
It's working until it comes time to save. It tells me it can't save because it's a read-only file system. I'm redownloading a live CD but it's taking forever.

---

### Post by Elfy on 2008-07-05
Do it from a root prompt - boot in recovery mode and then drop to the root prompt. But using sudo should let it save it without problem.

---

### Post by snkngshps on 2008-07-05
I'm actually doing both of those. I was suprised it wouldn't late me save it too. My shell definitely says root@JOSHUA: and I've been using sudo. I've tried editing fstab and saving and I'ved tried renaming the backup and both times it tells me it's a Read-only file system.

---

### Post by VMC on 2008-07-05
> **snkngshps said:**
> I'm actually doing both of those. I was suprised it wouldn't late me save it too. My shell definitely says root@JOSHUA: and I've been using sudo. I've tried editing fstab and saving and I'ved tried renaming the backup and both times it tells me it's a Read-only file system.

That doesn't make sense. type this from a Terminal:

```
ls -l /etc/fstab
```

---

### Post by snkngshps on 2008-07-05
When I do that it says:
-rw-r--r-- 1 root root 570 Jul  4 23:24 /etc/fstab

---

### Post by Elfy on 2008-07-05
Ok can you do this as well please

```
ls -l /etc/fstab*
```

If there is a fstab~ we cna use it to copy over

---

### Post by snkngshps on 2008-07-05
Well the ubuntu torrent finished so I was able to edit the file with the live cd. Thanks so much for the help. I still was never to figure out why it wasn't saving but I just gave it a reboot and it works fine. Thanks again!!!

---

