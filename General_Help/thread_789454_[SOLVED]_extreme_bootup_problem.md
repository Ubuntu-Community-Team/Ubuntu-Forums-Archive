---
title: "[SOLVED] extreme bootup problem"
date: 2008-05-10
forum: General Help
---

### Post by boyce1 on 2008-05-10
Hey,

i have forced disk check on bootup, however at 40% it freezes and reboots my computer. I have no idea what to do, is there anyway to prevent a fsck diskcheck?

im using 7.10, please help :(

---

### Post by ghost_ryder35 on 2008-05-10
[http://odzangba.wordpress.com/2007/11/26/skip-forced-disk-check-at-boot-on-ubuntu/](http://odzangba.wordpress.com/2007/11/26/skip-forced-disk-check-at-boot-on-ubuntu/)

---

### Post by boyce1 on 2008-05-10
im afraid that doesn't actually help. i cant get into ubuntu, how am i meant to edit files to change the amount of times there is a disk boot?

isn't there any type of command i can add to GRUB to stop it from doing a diskcheck? :(

---

### Post by MaindotC on 2008-05-10
I'm not sure about GRUB, but you can boot from a LiveCD and then edit the /etc/fstab file.

---

### Post by ghost_ryder35 on 2008-05-10
boot into recovery mode (is a default entry put in grub with a ubuntu install)

---

### Post by boyce1 on 2008-05-10
booting in recovery still comes up with a forced disk check.


where can i get the livecd? i've looked on the ubuntu site, but cant seem to find it :S

---

### Post by boyce1 on 2008-05-10
i still cant do anything.

how am i able to access the /fstab file without being able to get into gnome? :(

---

### Post by ghost_ryder35 on 2008-05-10
the regular ubuntu cd is a live cd.

---

### Post by ghost_ryder35 on 2008-05-10
> **boyce1 said:**
> i still cant do anything.
 
how am i able to access the /fstab file without being able to get into gnome? :(
 
You can skip the check with CTRL + C. Then press CTRL + D to resume bootup.

---

### Post by boyce1 on 2008-05-10
i've already tried CTRL C, but nothing happens. how do i boot into gnome from a livecd? i thought you had to install..

---

### Post by ghost_ryder35 on 2008-05-10
just pop it in and select the defaults.  have you tried the ctrl c before and during the dsk check?

---

### Post by boyce1 on 2008-05-10
i've tried during disk check, ill try before now.

i still don't understand with the livecd, which option do i go on? i can either install it again, or go to boot with first harddrive. if i go to boot with first hdd, it still goes into a disk check...

thank you for helping me out btw :)

---

### Post by boyce1 on 2008-05-10
ctrl C before the disk check only restarts the ubuntu load up splash thing..

is there anything weird with the disk check always starting at 12%? surely it shoudl start at zero... and it almost always freezes at 38%, then resets at either 39.9 or 40%. i've never heard of anything like this before, the only thing i can think of is a problem with sda1

---

### Post by ghost_ryder35 on 2008-05-10
> **boyce1 said:**
> ctrl C before the disk check only restarts the ubuntu load up splash thing..
 
is there anything weird with the disk check always starting at 12%? surely it shoudl start at zero... and it almost always freezes at 38%, then resets at either 39.9 or 40%. i've never heard of anything like this before, the only thing i can think of is a problem with sda1
agreed, probally some corrupt files.
if you got the standard install cd and not the alternate install cd it should say start or install like this, this is the option you want
[IMG]http://www.linuxinstallations.com/images/ubuntu_710/1-boot.JPG[/IMG]
 
 
if it looks like the one below this text then you have downloaded the alternate install cd and you will need to download the live cd
[IMG]http://ubuntulite.tuxfamily.org/files/pictures/alternateinstall.gif[/IMG]

---

### Post by boyce1 on 2008-05-10
hmm mines not like that, looks like i've got the alternate cd.

if i boot from LiveCD, will i have the same stuff on my computer? or will it be the same as a new install?

---

### Post by ghost_ryder35 on 2008-05-10
> **boyce1 said:**
> hmm mines not like that, looks like i've got the alternate cd.
 
if i boot from LiveCD, will i have the same stuff on my computer? or will it be the same as a new install?
when you boot the live cd you will have all of the applications available to you that you would have available in a fresh default ubuntu installation but it will not be installed on your computer it will only exsist in your RAM and cdrom drive so it is a great trouble shooting and rescue tool. when you boot into the live cd just issue this command and replace the location with your drive.  make sure the drive is not mounted when issuing this command.
```

sudo fsck /media/sda1

```

---

### Post by boyce1 on 2008-05-10
so i can make changes to root files and stuff using LiveCD, and save them to my hardrive using that command?

---

### Post by ghost_ryder35 on 2008-05-10
yep, as long as you specify the location to 'save'.  the fsck command will just run a check on the disk (and hopefully complete)

---

### Post by Herman on 2008-05-10
:) You can run e2fsck directly yourself better than fsck can run e2fsck.

The operating system is already trying to run fsck itself, it runs fsck -C -R -A -a. You can find out what that does by typing 'man fsck' into a terminal.

What most people don't realize about fsck is, it's really a file system check program that runs other file system check programs. fsck doesn't actually do the real work itself.
The file system program that fsck runs for an ext2 or ext3 file system is e2fsck.

By running e2fsck yourself directly, you will be able to run it with the full range of options available, meaning you're not limited to just the options fsck can use.

Try this one, this is my old favourite, I know it off by heart,
```
sudo e2fsck -C0 -p -f -v /dev/sda1
```That will probably actually fix the problem, and even if it can't, it will produce an output telling you what's wrong and advising you what to do next.

Regards, Herman :)

---

### Post by ghost_ryder35 on 2008-05-10
thats some awesome info :)

---

### Post by boyce1 on 2008-05-10
thanks a lot guys :) im just downloading the normal cd, so i should  be testing this out pretty soon :)

---

### Post by boyce1 on 2008-05-11
ok, i can't boot from the livecd, different problem i think.

i first had a problem booting ubuntu because of APIC not working, but i got around that by adding the startup command 'noapic acpi=off', which got the livecd a bit further.

however, after a while at the splash screen, everything seems to stop and i just get a black screen saying 

**udevd-event [2099]: run_program: '/sbin/modprobe' abnormal exit**

followed by a load of buffer i/o errors and end_requests of fd0 device

ubuntu just doesn't like me?

---

### Post by boyce1 on 2008-05-11
OK...

i managed to eventually get the liveCD working, using the command

**all_generic_ide noapic acpi=off**



did the disk check in terminal, left for a while then came back it said:

[B]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
Error reading block 34064255 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 17023325.  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)[/B]

gonna do a manual fsck and see what happens...

---

### Post by boyce1 on 2008-05-11
SOLVED

thanks, after doing the manual disk check it found and fixed some problems :D


thanks again!

---

### Post by Herman on 2008-05-11
Okay, cool! :)

---

### Post by MaindotC on 2008-05-11
I think some Thanks are in order...

---

