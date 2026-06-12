---
title: "error loading operating system"
date: 2007-10-26
forum: General Help
---

### Post by odindio on 2007-10-26
I just loaded xubuntu onto my amd-duron pc, and put it into hibernate.  I tried to power up and I get error loading OS.  Huh? :(

---

### Post by bobyy on 2007-10-26
You have some more info...?what error ? give us a clue:)

---

### Post by odindio on 2007-10-26
booting from local disk....
error loading operating system

---

### Post by bobyy on 2007-10-26
somehow you`MBR is wanished...tri to boot with Live-cd and reinstall you MBR.

---

### Post by bobyy on 2007-10-26
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
try with this..
7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps.

---

### Post by bobyy on 2007-10-26
Here you have a good how to:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by odindio on 2007-10-26
I don't really know that much about linux.  So I reall wouldn't know how to fix the mbr

---

### Post by odindio on 2007-10-26
i did restart it up with the disc though

---

### Post by bobyy on 2007-10-26
? something new.....let us know if you solved.

---

### Post by gdoutch on 2007-10-28
I have the same problem, (after installing gutsy with Win XP) but when I type
> find /boot/grub/stage1

I get 

> Error 15: File not found


Any clues?

---

### Post by gdoutch on 2007-10-28
This is my fdisk -l 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1d7f5ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2664    21398548+   7  HPFS/NTFS
/dev/sda2   *        2665        7114    35744625   83  Linux
/dev/sda3            7115        7296     1461915    5  Extended
/dev/sda5            7115        7296     1461883+  82  Linux swap / Solaris


and grub doesn't appear in my /boot dir either.

---

### Post by sandysandy on 2007-10-28
> **gdoutch said:**
> I have the same problem, (after installing gutsy with Win XP) but when I type


I get 



Any clues?

u may like to try to find the location of your file [COLOR="Blue"]stage 1[/COLOR] manually.
go to places (on top bar of ur desktop, between applications & System) and select  my computer. select ur linux partition in the window and press enter. select boot folder in this and press enter. u will find grub in this boot folder.


by the way are you booting from hard disk or from live cd.

regards:guitar:

---

### Post by gdoutch on 2007-10-28
Thanks sandy, 

edit - I had to use the live CD following an install as I was getting 'error loading operating system'.

Currently, I've used GParted on my live CD to set my boot flag back to /dev/sda1 so I can access my WinXP installation with no problems - but I'm without access to my gutsy install :(

So the question now is how do I get grub installed? Most of the help I've seen seems to rely on finding stage 1, but I'm pretty certain I don't have it.

---

### Post by sandysandy on 2007-10-29
> **gdoutch said:**
> Thanks sandy, 

edit - I had to use the live CD following an install as I was getting 'error loading operating system'.

Currently, I've used GParted on my live CD to set my boot flag back to /dev/sda1 so I can access my WinXP installation with no problems - but I'm without access to my gutsy install :(

So the question now is how do I get grub installed? Most of the help I've seen seems to rely on finding stage 1, but I'm pretty certain I don't have it.

may be these links may help:-

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

regards

---

### Post by gdoutch on 2007-10-29
Thanks for you help Sandy, but my problem was something else.

When I first installed ubuntu, I went throught the partition wizard by choosing the default drive names that were assigned to my windows and ubuntu partitions, which were:

sda1 : /media/disk1
sda2 : /media/disk2

Which was causing me all my Grub problems.


So I went through the installation again this time making sure that:

sda1 : /windows
sda2 : /

And everything works! :D :D :D

---

### Post by sandysandy on 2007-10-29
Great:)

---

### Post by odindio on 2007-12-28
I somehow missed bobyy's posting, so I gave up and did a reinstall, so I have no  answer on wether this worked.

---

