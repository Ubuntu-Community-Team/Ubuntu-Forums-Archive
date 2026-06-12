---
title: "Stuck in a password loop after upgrade to 12.10"
date: 2013-11-26
forum: General Help
---

### Post by lynyl on 2013-11-26
After an upgrade to 12.10, I found that I could not get past the password screen. I would enter my password, but the password page would just come up again. If I entered a deliberately wrong password, it would say that it was wrong, but when I entered the correct one - it would just loop back to the password screen. So I tried my guest login, which has no password, but it would just change to a colored screen with nothing on it

So I hit the forums. 
I tried "password lyn" and then entered a new password (blind) two times and got "authentication token manipulation error" with password unchanged. Then I tried "mount -o remount," followed by a " /"  (sorry this tablet and its auto-formatting changes the code but the whole command is one code line.) Anyway, with this I changed the password successfully BUT still it looped back to the password screen.
I updated the grub boot loader in the recovery mode but no difference.
Also in recovery mode, I did the "repair broken packages" and the system had a number of updates (I had been away from my home and computer for a number of days after this problem started, though I had done all the updates immediately prior to the upgrade attempt) and came back with a "failed to fetch". But the top right menu bar on the password screen says I have a wired internet connection.[B]
So - can anybody help? [/B]I have used Ubuntu since 10.01 and Linspire before that and can use the terminal - but directions need to be clear and step-by-step. Any suggestions you have I will greatly appreciate.

---

### Post by varunendra on 2013-11-26
Have you checked free space? If unsure, show us the output of -
```
df -h
```

---

### Post by lynyl on 2013-11-26
I have 36G free space.

---

### Post by varunendra on 2013-11-26
I would like to see the output myself. And can you boot into any of the virtual tty's (Ctl-Alt-F1 through F6)?

Also, is the whole Ubuntu installation using a single partition (/) or multiple ones (for example /, /boot, /home etc.)?

If it is on a single partition and you are sure there is no space issue, it can be an .Xauthority file issue. You can confirm/correct that from a live session running off a live cd/usb.

There can be some other reasons as well, but these two are most common for login failure.

---

### Post by lynyl on 2013-11-27
I can only get into F2 (Bios).  I only had the one partition (here I am assuming  that since I did not install a partition, that Ubuntu did not install one on upgrade). I sure wish I  could send you any output from the root sessions - but no way to get them off the hung-up computer to my Kindle fire. 
So is the next step  is to use a live CD/usb? Since I was loading 12.04- is that what I would use?  Do you know the site where I can download it? And how do I use it to diagnose and fixes the problem? 
Thank you so very much!

..

---

### Post by jeanjd63 on 2013-11-27
Hello,

You can boot in recovery mode, open a root session, make / in rw mode :
**mount -o remount,rw  /**
then you can delete 2 files in your user environment :
[B]cd  /home/lyn
rm  .Xauthority .ICEauthority[/B]

Then you reboot

---

### Post by lynyl on 2013-11-27
Ok I did the "mount -o remount,rw /"  command. Then I didn't do the "cd /home/lyn" command as that seemed to be aimed at the cd player, but Idid the last command:  "rm .Xauthority .ICEauthority" and the repl came back that they couldn't be removed as there were no such files. Any thoughts?)

---

### Post by QIII on 2013-11-27
Hello!

The cd command changes the directory.  You need to issue that command to move to the directory where those files are found so you can use the next command to do the file operation.

Cheers!

---

### Post by jeanjd63 on 2013-11-28
> **jeanjd63 said:**
> Hello,

You can boot in recovery mode, open a root session, make / in rw mode :
**mount -o remount,rw  /**
then you can delete 2 files in your user environment :
[B]cd  /home/lyn
rm  .Xauthority .ICEauthority[/B]

Then you reboot


You retries and [B]do all commands
[/B]Bye

---

### Post by lynyl on 2013-11-28
I entered all the commands. After the "cd /home/lyn" command, it showed 
   "root@lynslinux:/home/lyn#" and I added the "rm .Xauthority .ICEauthority" command
   It came back saying that each of these files could not be removed as there was no such file or directory.
And no change on reboot.

---

### Post by varunendra on 2013-11-28
> **lynyl said:**
> I entered all the commands. After the "cd /home/lyn" command, it showed 
   "root@lynslinux:/home/lyn#" and I added the "rm .Xauthority .ICEauthority" command
   It came back saying that each of these files could not be removed as there was no such file or directory.
And no change on reboot.

Those files should have been there, but that aside, are you trying to log in as root?? Enabling the root account is not required and absolutely not recommended.

Which account are you having problems with? lyn or root or some other one?

Booting with a live cd/usb can make things a lot more easier by letting you get and post all the outputs we ask for here.

You can download the desired ISO (I recommend 12.04.3) via torrent to ensure a faster download and its data integrity. Official site for torrents : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

Burn the downloaded ISO to a cd or create a live usb with it, boot with it and browse to the home folder of the user who you are having problem with. Press "Ctrl-H" to view hidden files and see if you can find the .Xauthority and .ICEauthority files in it. If not, post back and confirm you are using the live CD/USB and we may ask for more outputs which you can easily post from the live session.

**PS:** I personally am not sure if deleting the .ICEauthority file is safe. I would make a backup before deleting it.

---

### Post by jeanjd63 on 2013-11-29
Hello,
Could you gave the complete return of this commands :
[B]df  -h
df -i[/B]
and 
**cd  /home/lyn**
then[B] 
ls -la   .*autho*

[/B]Bye

---

