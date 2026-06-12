---
title: "Can Not Boot!"
date: 2007-05-30
forum: General Help
---

### Post by halfmoon7 on 2007-05-30
Alright, I installed using Wubi, and everything was going perfectly until I turned on the Desktop Effects (I think thats what its called). I turned it on and my desktop was enlarged so that I could not see the top or bottom task bars. After this I forced a shutoff on my laptop (probably shouldn't have...) and now I can boot neither windows nor ubuntu. I turn my laptop on and it takes me to the boot menu asking me to choose to boot ubuntu or windows, and when I click one, it immediately restarts my laptop and takes me back to the boot menu. I have already tried all of the safe modes and everything, but it just keeps taking me back to the boot menu.
   Please Help!!

---

### Post by Pragmatist on 2007-05-30
If you can get a LiveCD, then you can access your system and we can help you edit your bootloader's files to get you up and running.

---

### Post by Death_Sargent on 2007-05-30
Yes that sounds like the best route as I am willing to bet linux is nor teribly messed up.

If you can't get a liveCD or are not paitent enought for the ones you get cia free mail order then you want to look into finding a solution to repairing the windows boot loader

---

### Post by halfmoon7 on 2007-05-30
Thanks, however, I already have a boot CD, but it does not work on my laptop for some reason. That is how I tried to install Ubuntu in the first place, but since it didn't work, I tried wubi. Any other suggestions? ;)

---

### Post by Pragmatist on 2007-05-30
> **halfmoon7 said:**
>  Any other suggestions? ;)

Yes, you can use a different LiveCD, like Knoppix.  You can download it and burn it to disk.

Other than that, the only other thing I could think of would be to put a working computer on a router with the broken computer.  Then, ssh into the broken machine and try and fix it that way.  However, this method probably won't work as you need to have the ssh daemon running on the broken machine....but you can't get into the broken machine...etc...

The only way I know of fixing your computer is to use a LiveCD or boot disk.  You have to access the machine in order to fix it.

---

### Post by Pragmatist on 2007-05-30
Incidentally, what happened when you tried the Ubuntu LiveCD?  Did you make sure to go into your BIOS put CD first in the boot order?

---

### Post by halfmoon7 on 2007-05-30
When I put in the CD, (I did set CD/DVD Drive as the 1st in the boot order) the computer buzzes for about 5 sec like its working on it, but then just goes back to the boot menu. Before the problem it would work on the CD, then just start booting windows. I do have a slax CD, and just tried it. You think you could help me through that? Thank You!

---

### Post by Pragmatist on 2007-05-30
> **halfmoon7 said:**
> ...I do have a slax CD, and just tried it. You think you could help me through that? Thank You!

I'll try and help.  The first thing you need to do is get to a terminal.  I've never used slax, but I'm sure there is some sort of GUI where you can go to a menu and pick a terminal to run.  Next, you want to find your hard drive (remember, slax is running off a CD).  Run this command to see if your hard drive is already mounted:
```
mount
```
If you don't see it (probably /dev/hda or /dev/sda) then look for mount points at /media:
```
ls -l /media
```
If you see something like "hda", then you want to mount your hard drive at that mount point:
```
sudo mount /media/hda
```

Let us start with that.  After you've found your hard drive, the rest should be easier to explain.

---

### Post by halfmoon7 on 2007-05-30
Okay, Ive got: /dev/pts, /dev/hdc1, /dev/hdc2, and /dev/hdc3 for the 'mount' command and I get nothing for the 'ls -l /media' command.

---

### Post by Pragmatist on 2007-05-30
What do get from this command (the l in -l is a lowercase L):
```
ls -l /dev/ | egrep '[hs]d'
```

---

### Post by halfmoon7 on 2007-05-30
I get a lot of info... what am I looking for?

---

### Post by Pragmatist on 2007-05-31
It shouldn't be that much.  I'm looking for all files in the /dev directory that begin with either hd or sd  For example, here is the output for my system:
> desktop:~$ ls -l /dev/ | egrep '[hs]d'
lrwxrwxrwx 1 root  root           3 2007-05-30 12:38 cdrom -> hdd
lrwxrwxrwx 1 root  root           3 2007-05-30 12:38 cdrw -> hdd
lrwxrwxrwx 1 root  root           3 2007-05-30 12:38 dvd -> hdd
lrwxrwxrwx 1 root  root           3 2007-05-30 12:38 dvdrw -> hdc
brw-rw---- 1 root  disk      3,   0 2007-05-30 12:38 hda
brw-rw---- 1 root  disk      3,   1 2007-05-30 12:38 hda1
brw-rw---- 1 root  disk      3,   2 2007-05-30 12:38 hda2
brw-rw---- 1 root  disk      3,   3 2007-05-30 12:38 hda3
brw-rw---- 1 root  disk      3,   5 2007-05-30 12:38 hda5
brw-rw---- 1 root  disk      3,   6 2007-05-30 12:38 hda6
brw-rw---- 1 root  cdrom    22,   0 2007-05-30 12:38 hdc
brw-rw---- 1 root  cdrom    22,  64 2007-05-30 12:38 hdd
lrwxrwxrwx 1 root  root           4 2007-05-30 12:36 mybook -> sda1
crw-rw-rw- 1 root  tty       2,  61 2007-05-30 12:38 ptysd
brw-rw---- 1 root  plugdev   8,   0 2007-05-30 12:36 sda
brw-rw---- 1 root  plugdev   8,   1 2007-05-30 12:36 sda1
brw-rw---- 1 root  plugdev   8,  16 2007-05-30 12:36 sdb
brw-rw---- 1 root  plugdev   8,  32 2007-05-30 12:36 sdc
brw-rw---- 1 root  plugdev   8,  48 2007-05-30 12:36 sdd
brw-rw---- 1 root  plugdev   8,  64 2007-05-30 12:36 sde
crw-rw-rw- 1 root  tty       3,  61 2007-05-30 12:38 ttysd


---

### Post by Pragmatist on 2007-05-31
I was trying to save you some typing, but my command might give more output than we need.  Use these instead:

```
ls -l /dev/hd*
```
```
ls -l /dev/sd*
```

---

### Post by halfmoon7 on 2007-05-31
Alright, well I am not on the internet on my laptop, but on my desktop so I can not copy paste, but I will type it out:

lrwxrwxrwx 1 root root               3 May 30 18:30 cdrom -> hda
lrwxrwxrwx 1 root root               3 May 30 18:30 cdrom0 -> hda
lrwxrwxrwx 1 root root               3 May 30 18:30 dvd -> hda
lrwxrwxrwx 1 root root               3 May 30 18:30 dvd0 -> hda
brw-rw---- 1 root cdrom      3,     0 May 30 18:30 hda
brw-rw---- 1 root disk       22,     0 May 30 18:30 hdc
brw-rw---- 1 root disk       22,     1 May 30 18:30 hdc1
brw-rw---- 1 root disk       22,     2 May 30 18:30 hdc2
brw-rw---- 1 root disk       22,     3 May 30 18:30 hdc3
lrwxrwxrwx 1 root root               5 May 30 18:30 ptysd -> pty/m
lrwxrwxrwx 1 root root               5 May 30 18:30 ttysd -> pty/s
crw-rw---- 1 root root       10,  130 May 30 18:30 watchdog

---

### Post by halfmoon7 on 2007-05-31
for those last two commands i get:

brw-rw---- 1 root cdrom   3, 0 May 30 18:30 /dev/hda
brw-rw---- 1 root disk     22, 0 May 30 18:30 /dev/hdc
brw-rw---- 1 root disk     22, 1 May 30 18:30 /dev/hdc1
brw-rw---- 1 root disk     22, 2 May 30 18:30 /dev/hdc2
brw-rw---- 1 root disk     22, 3 May 30 18:30 /dev/hdc3

and for ls -l /dev/sd* I get nothing

---

### Post by Pragmatist on 2007-05-31
It looks like your hard drive is at /dev/hdc  Let's see the size of the /dev/hdc partitions just to make sure:

```
df -h /dev/hdc*
```

If using the * doesn't work, just do 3 seperate commands.  You only need to note the size of the partitions and verify that this is your hard drive (this step isn't 100% necessary, but it's good to know where we're at):
```
df -h /dev/hdc1
```
```
df -h /dev/hdc2
```
```
df -h /dev/hdc3
```

---

### Post by halfmoon7 on 2007-05-31
The first command worked:

File System                       Size       Used     Avail   Use %  Mounted on
-                                          0            0           0          -            /dev
/dev/hdc1                          40M      7.2M     32M      19%   /mnt/hdc1
/dev/hdc2                          34G      33G      744M     98%   /mnt/hdc2
/dev/hdc3                          3.5G     2.7G     911M     75%   /mnt/hdc3

---

### Post by Pragmatist on 2007-05-31
Ok, this looks like your hard drive right?  So, we need to do the mount command again, and this time you need to give me a little more information.

```
mount |grep hdc*
```

Here is my output, we need all the information:
> desktop:~$ mount |grep hda*
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
/dev/mapper/hda3 on /media/kubuntu type ext3 (rw,errors=remount-ro)

/dev/hda1 is a partition of my hard drive. It is mounted on /  which is known as root as it is the head of the whole Linux file system hierarchy.  The file system is of type ext3 and it is mounted read-write (rw).  So we need most of the information on each line.  You should have 3 lines, one for each of the three /dev/hdc partitions.

---

### Post by halfmoon7 on 2007-05-31
Okay:

/dev/hdc1 on /mnt/hdc1 type vfat (rw)
/dev/hdc2 on /mnt/hdc2 type ntfs (ro)
/dev/hdc3 on /mnt/hdc3 type vfat (rw)

Thats everything I get.

---

### Post by Pragmatist on 2007-05-31
Ok, what do you get when you type this:

```
ls /mnt/hdc3/boot
```

Edit:  You don't have to give me everything.  Do you see these sorts of files:
> abi-2.6.15-23-386     config-2.6.15-26-386      initrd.img-2.6.15-26-386      initrd.img-2.6.20-15-386.bak  System.map-2.6.20-15-386
abi-2.6.15-26-386     config-2.6.15-27-386      initrd.img-2.6.15-27-386      memtest86+.bin                vmlinuz-2.6.15-23-386
abi-2.6.15-27-386     config-2.6.17-10-386      initrd.img-2.6.17-10-386      System.map-2.6.15-23-386      vmlinuz-2.6.15-26-386
abi-2.6.17-10-386     config-2.6.17-11-386      initrd.img-2.6.17-10-386.bak  System.map-2.6.15-26-386      vmlinuz-2.6.15-27-386
abi-2.6.17-11-386     config-2.6.20-15-386      initrd.img-2.6.17-11-386      System.map-2.6.15-27-386      vmlinuz-2.6.17-10-386
abi-2.6.20-15-386     grub                      initrd.img-2.6.17-11-386.bak  System.map-2.6.17-10-386      vmlinuz-2.6.17-11-386
config-2.6.15-23-386  initrd.img-2.6.15-23-386  initrd.img-2.6.20-15-386      System.map-2.6.17-11-386      vmlinuz-2.6.20-15-386


---

### Post by halfmoon7 on 2007-05-31
No, I do not. "No such file or directory" is what I get.

---

### Post by Pragmatist on 2007-05-31
Ok, I'm sorry, I didn't fully understand what WUBI is.  I just thought it was a program to help you install ubuntu from within windows.  Actually, WUBI installs ubuntu as a file within windows.  So, I now know where we need to look.  Following some of the ideas here, (and on the WUBI website)

[https://answers.launchpad.net/wubi/+question/7418](https://answers.launchpad.net/wubi/+question/7418)

We need this file:   c:\wubi\boot\grub\menu.lst
However, in slax, c: will be represented by one of those /dev/hdc partitions.  Probably /dev/hdc2

Try this:
```
sudo cp /mnt/hdc2/wubi/boot/grub/menu.lst ./mymenu.lst
```Then copy the file "mymenu.lst", which will be in the same directory your currently in, to a floppy or cd, if you can, and then attach the file here.

Edit: If you get a "no file found" type of message, then do the same command with hdc1 and then hdc3.  It has got to be in one of those three partitions.

---

### Post by halfmoon7 on 2007-05-31
Okay I tried all three. hdc1 and hdc3 say no such file or directory; however, hdc2 gives me the message 'input/output error'. I double checked my typing too... :)

---

### Post by Pragmatist on 2007-05-31
Strange.  What do you get if you just try to list the contents of /mnt/hdc2

```
ls /dev/hdc2
```

---

### Post by halfmoon7 on 2007-05-31
It just gives me '/dev/hdc2' (It is in yellow font)

---

### Post by Pragmatist on 2007-05-31
I'm sorry, I was tired. This is the command:
```
ls /mnt/hdc2
```

---

### Post by halfmoon7 on 2007-05-31
Okay, it says '/bin/ls: reading directory /mnt/hdc2: Input/output error'

---

### Post by Pragmatist on 2007-05-31
Let's try it with sudo  and do it for all three partitions (hdc1, hdc2, hdc3)

```
sudo ls /mnt/hdc1
```
```
sudo ls /mnt/hdc2
```
```
sudo ls /mnt/hdc3
```

---

### Post by halfmoon7 on 2007-05-31
For sudo ls /mnt/hdc1 I get a whole bunch of stuff (9 rows with 9 items in each row); for sudo ls /mnt/hdc2 I get 'input/output error'; and for sudo ls /mnt/hdc3 I get: autoexec.bat   bat   bin   command.com   config.sys   img   io.sys   msdos.sys   src1   src2   src3   src4   src5.

---

### Post by Pragmatist on 2007-05-31
Probably the best approach now is to use a DOS boot floppy and uninstall WUBI by deleting these directories/files:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Specifically, this part:

>  
  **How do I manually uninstall Wubi?**

  Remove C:\wubi, C:\grldr, C:\grub.exe, C:\menu.lst. Then edit C:\boot.ini and delete the Wubi line. C:\boot.ini is normally protected. To edit it, go to control_panel > system > advanced > startup_and_recovery and press Edit. 

After that you can try WUBI again if you want.  Personally, I would not do that!  WUBI is a nice idea, but it is Beta software.  Probably better to wait until they have reduced the bugs and mature to a stable version.

A normal dual-boot is much easier, actually.  The methods of troubleshooting that we used here, would work very well with a normal dual-boot, since Linux would be on its own partition.  Right now you only have windows partitions with your main partition being NTFS and read-only.  It might be possible to continue using the Linux LiveCD, but using a Windows (i.e. DOS)  boot disk makes the most sense at this stage.  It should only be a matter of booting the machine, and erasing the above files and directories.  If you really don't want to uninstall it, the DOS boot disk will still give you access to the configuration files we need (the ones we've been looking for the last couple of days).  You could try editing the config files and fix the current installation.  However, this last approach is definitely not the simplest approach.

---

