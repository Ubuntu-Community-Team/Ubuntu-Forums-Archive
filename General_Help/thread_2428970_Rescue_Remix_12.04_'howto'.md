---
title: "Rescue Remix 12.04 'howto'"
date: 2019-10-11
forum: General Help
---

### Post by batgirl2 on 2019-10-11
My ubuntu 18.04lts laptop bootup circus act has returned - the one that "fsck /dev/sda1" fixed. (circus act is: boot, hold down power button part way thru, boot again and all is normal... until you boot next time and it will freezeup if you don't stop the initial bootup part way thru and begin boot again...)  Got Rescue Remix v12.04 iso on a CD, boots off of it fine... comes up with nice graphic and "BOOT" at the bottom.... don't know how to use this thing... documentation is severely lacking and the little there is is so cryptic I glaze over :-\  note: once in Ubuntu 18.04lts I try to go to terminal and run fsck but get mount error.. then try umount /dev/sda1 but get busy error...really lost ;-}  I can get to the grub prompt during bootup but it doesn't recognize fsck....  Vista64 laptop's working fine though and helping me during this linux mess :-D  Just would like to get to where I can run 'fsck /dev/sda1' again....

---

### Post by QIII on 2019-10-11
Is [this thread]("https://ubuntuforums.org/showthread.php?t=2421994") about your "bootup circus"?

---

### Post by batgirl2 on 2019-10-11
> **QIII said:**
> Is [this thread]("https://ubuntuforums.org/showthread.php?t=2421994") about your "bootup circus"?  No - bootup circus will fix itself like last time IF I can get fsck to run.... need to get to where 'fsck /dev/sda1' will run and repair crap... thought 'rescue remix' would help by getting where fsck will run but unable to figure it out rescue remix w/o good howto.

---

### Post by rsteinmetz70112 on 2019-10-11
Do you have a DVD or USB stick? It would be easier to use a live DVD. Then you don't have to boot the existing installation just run fsck from the live session and reboot.

---

### Post by batgirl2 on 2019-10-11
like I say above, got this 'rescue remix CD' (similar to live CD) that comes up with this prompt "Boot:" that I don't know what to do with... the laptop is old tech - CD, no DVD :-|

---

### Post by rsteinmetz70112 on 2019-10-11
I'm not familiar with the 'rescue remix CD' it seems to be trying to boot the Ubuntu installed on the hard drive and running into problems.  Does the computer have a USB Slot? If so you can either make a live USB stick or use a USB DVD drive to open a live session.  An older Ubuntu live CD may work but depending on the file system on the existing install may not work.

---

### Post by batgirl2 on 2019-10-12
[https://archiveos.org/ubuntu-rescue/](https://archiveos.org/ubuntu-rescue/)

---

### Post by yancek on 2019-10-12
>  once in Ubuntu 18.04lts I try to go to terminal and run fsck but get mount error.. then try umount /dev/sda1 but get busy error

From the above it would seem you are trying to run fsck on the system you are booted to and running.  That won't work.  You need to use something on a CD/DVD/USB and probably the best option would be the medium you used to install 18.04.  I'm not familiar with the Rescue REmox but looking briefly at the site you linked to, it indicates it is designed for 12.04 which is over 7 years old and the most recent date on that page is nearly 4 years ago.  If you have the Ubuntu install medium, that would be the simplest/best choice.

---

### Post by batgirl2 on 2019-10-12
Bought laptop with ubuntu 16.10 preinstalled, and have just been upgrading to 17.04, 17.10, then 18.04LTS (then stopped)... no CD/DVD on ubuntu and since I'm 32-bit, there's no 32-bit iso for 18.04LTS... as far as rescue remix 12.04, the info just says works on Linux, not just ubuntu, and not any other additional requirements for the OS. Don't think it it limited to 12.04 and older ubuntu... my G4L (Ghost for Linux ) uses several older kernels and still does Great imaging my other stuff w/o issues...

---

### Post by yancek on 2019-10-12
The quote below from your original thread.

> Got Rescue Remix v12.04 iso on a CD, boots off of it fine... comes up with nice graphic and "BOOT" at the bottom...

See the link below, scroll about half-way down the page and it has images of the screen and shows what you enter there.

[https://linuxlandit.blogspot.com/2011/07/ubuntu-rescue-remix-is-gnulinux-live.html](https://linuxlandit.blogspot.com/2011/07/ubuntu-rescue-remix-is-gnulinux-live.html)

---

### Post by batgirl2 on 2019-10-12
> **yancek said:**
> See the link below, scroll about half-way down the page and it has images of the screen and shows what you enter there.[https://linuxlandit.blogspot.com/2011/07/ubuntu-rescue-remix-is-gnulinux-live.html](https://linuxlandit.blogspot.com/2011/07/ubuntu-rescue-remix-is-gnulinux-live.html)  The video says its remix, but launch it and it goes on about running 'Freemind'.... wants to do unspeakable things to the partition or something! nice music....  Last time this boot issue happened, it finally totally crashed but rebooting kept coming up to some prompt that let 'fsck /dev/sda1' run - asked a bunch of questions, said yes to all, and boot got normal for a month until it went non-responsive the other day, and now back to the circus act until it finally crashes and gives me opportunity to run that command ;-)

---

### Post by yancek on 2019-10-12
Not sure what 'video' you are referring to but the link I posted has a number of images including at least 2 which show the screen that has boot: at the bottom and just above that it tells you that to use the default live Rescue Remix system, you type the word live in lowercase letter and hit the Enter key.  THat should get you to a place where you can use the various software included on the CD and I would think you could use a terminal and run fsck from there.

---

### Post by batgirl2 on 2019-10-13
Will do that next and report back ;-)

---

### Post by batgirl2 on 2019-10-13
typed 'live' and got an error amongst the loaded items, - so instead on next boot tried something I read about and selected the 'advanced options' choice on the purple menu, then did the 'recovery mode' choice - let it run and on next boot - it's back to booting normally (w/o the hang/freezeup/circus act) again! Again, don't really know how it got 'fixed', but grateful it did... wonder what the upstart choice does :-}

---

### Post by rsteinmetz70112 on 2019-10-14
Lubuntu still has a 32 bit iso you could use for a live system either on DVD or USB. It's also geared for older hardware and actively developed.

---

