---
title: "initrams commands"
date: 2014-01-03
forum: General Help
---

### Post by charitosha on 2014-01-03
I was wondering what all these initramfs build-in commands mean?
does anyone know a site which describes each command?
or is it possible, while initramfs is running, to view the details of a command?

p.s. when i type /dev or /usr or / it always say permission denied why is that???

---

### Post by Bashing-om on 2014-01-03
charitosha; Hi !

These will shed some light on the role of "initramfs" :
[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)
[https://wiki.ubuntu.com/Initramfs](https://wiki.ubuntu.com/Initramfs)
[https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot)

And for access/permission: Why, read:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[INDENT][INDENT]just my little bit to help[/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-04
whao that's some very interested sites!!!
Want to ask one quick question... :razz:
with the ls command you can list the devices and/or files but how can someone list the hard-disks and the partitions of those hard-disk?

---

### Post by egeezer on 2014-01-04
To list partitions on a hard drive, use:
```
sudo parted /dev/sda print
```

Hit Enter, then your password, then Enter again.

---

### Post by charitosha on 2014-01-04
> **egeezer said:**
> To list partitions on a hard drive, use:
```
sudo parted /dev/sda print
```

Hit Enter, then your password, then Enter again.

when i type:  s:```
sudo parted /dev/sda print
```
,i get: ```
/bin/sh: sudo: not found 
```
The thing is that i'm not like in the Terminal when ubuntu has launched but in initramfs. I think because of that i cannot write as a sudo.
But besides that i think that when in initramfs there should be a command from which you can see info about partitions of a hard-disk and about the number of hard-disk placed.
Can anyone tell me which one is it???

P.S. Also can anyone explain me the difference between the GRUB and initramfs(in few words)

Looking forward for your help

---

### Post by Bashing-om on 2014-01-05
charitosha; Hey,

Let me try and explain it like this:
Grub = Grand Unified Bootloader, It's only job (a big one !) is to load the operating system; One may invoke another layer at the grub prompt, say, for instance, a very minimalistic text editor or an even more minimalistic console interface.

The initramfs prompt is also a Very minimalistic console interface, supporting only a few commands - sudo is not one of them. At the intiramfs prompt enter "help" - without the quotes for a list of supported commands. Just enough here to rescue the system and/or see what is wrong.

Your questions beg my question, are you stuck at the initramfs prompt ?

What you need, in order to communicate fully with your system, is a Command Line Interface. Some call this a terminal, other may refer to it as a console. The full power of your system is unleashed from the CLI ! I do prefer to deal with my system from the CLI, and I choose to boot my system to a CLI as I adhere to the KISS principal . From that interface I launch whatever I want to activate. You will do things in a different manner .

[INDENT][INDENT]ask and 
[INDENT][INDENT][INDENT]thou shalt receive
 [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-06
Bashing-om you said that " At the intiramfs prompt ... Just enough here to rescue the system and/or see what is wrong".
The thing is that i get a no oparating device. (I have a win7 starter, and a ubuntu installation that went bad... I'm a noobie what do you expect? 8-[ ) 
My main problem : When in initramfs i was able to locate my hard drive and its partitions but i need some guidance in how to boot OS from there.--- i mean i has to BE there, normally nothing should be deleted. 
(on my hard drive along Windows i also have ubuntu Live, i mistakably burnt it to to a hd partition instead of my USB).

---

### Post by Bashing-om on 2014-01-06
charitosha; Hey;

Show us what we are working with.
Boot from the liveUSB -> activate a terminal and;
Post the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
to show the partitioning on the hard disk(s). Then we will look at if/where grub (Grand Unified Bootloader) is installed. Once these are known we can advise on booting into the ubuntu operating system.
If it turns out you have GPT partitioning will have other tools to look at that partitioning.

This "presumes" you intend to install ubuntu onto a hard disk, we are looking to see that the required partitioning has been done. Then we will look at the grub situation. There is no point in doing anything else until we know that ubuntu has been installed and that all we are dealing with is a matter of directing where the files are located.

[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-07
Bashing-om there is an issue... i cant even run liveusb (lubuntu via unetbootin).

when i try to install it i get after a while error 1 or error 10

when to try without installing the screen display goes black/grey and that's that.

the only thing that i can do is to go to the help option of UNetbooting blue page. then i'm in the busybox and initramfs is on. That's why i said that most likely(if possible) i'll have to boot from initramfs. in my hdd i have win7 starter and (mistakebly burnt) ubuntu Live in another partition... 

please people i need some guidance, i can't do it by myself... ](*,)

---

### Post by Bashing-om on 2014-01-07
charitosha;Hey;

Let's be clear about the needs and your goals.
As It stands now, you can not boot to "try ubuntu" from the install usb. In order to install, "try ubuntu" must be functionable. What we see here many times in this situation is that a graphics driver is not available. One can force the system to use a lower level "workable" driver if this is the condition. We need to know what graphics card you have to advise on the procedure to boot to a desk top.

Background stuff:
Did you verify the .iso file ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
<Many people have problems with unetbootin, are there any other alternatives ? >
Burn the .iso file as an IMAGE to disk: A number of options for your consideration :
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/Troubleshooting](https://help.ubuntu.com/community/Troubleshooting)
Just so you are absolutely sure of the install medium.
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

Now we are ready to make the install, and troubleshoot any difficulties. Standard procedures to do this are in place and have nothing to do with having to invoke "initramfs" at this point.

Once we know what it takes to boot into "try ubuntu", better advise is available to boot into the install system.

We will get you up and 
[INDENT][INDENT][INDENT]running ubuntu
[/INDENT][/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-07
md5 check sums are the same. some of the links that you showed me i've already read...
i don't know if it's possible to make a recovery disk on a machine that i cannot boot into an OS.
and i want to tell how(i think) it happened that i get no operating device detected:
when i mistekably burnt ubuntulive into my hdd(there is only one), then every time i switched on the netbook it automatically run ubuntulive and not boot to win7. 
Then (if i remember correctly) in gparted i took away the boot flag from the partition where ubuntulive was, but i didn't put it in the partition where win7 was (i could see all the partitions on that table).
after that point i get no os device detected.
that's why i'm at a loss (on top of that i have some important documents in Windows, don't want to lose them if possible)

---

### Post by Bashing-om on 2014-01-07
charitosha; Hey.

OK, Here is what is.

You need to (re-)install grub to the MBR of the hard disk. In order to do this the best course is to boot up the liveUSB;
determine what partition is what;
mount ubuntu's install "root" partiton from the liveUSB;
Install grub using the files from the liveUSB onto the install's MBR (automagic);
update-grub to pickup and chainload Windows.

ELSE: How about using the Window's recovery disk and installing Windows' bootloader ( will not recognize ubuntu, however)?

Once you have a booting liveUSB (prefer a DVD. personal preference) ->

[INDENT][INDENT][INDENT]a piece of cake
[/INDENT][/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-08
Bashing-om althought it sounds easy there might be a problem...
in order to install grub to the MBR, i have to find MRB first... right?
 BusyBox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4.1) built-in Shell (ash)
my root directory: ```
(initramfs) ls 
dev usr run conf init lib proc var 
root scripts bin sbin etc sys tmp 
``` 



Q1: does the MBR has to be in /boot?  
Q2: Is it possible to find MRB via /sys? or from somewhere else?
 Q3:why i have different root directory than [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html), is root directory like machine-specific?
Q4: is init the same as initrd?
i can't cd to init.
/root is totally empy via ls
/run is totally empy via ls  Q5: why are /root and /run empty?
/tmp is totally empy via ls Q6: is it because there is nothing temporary to be saved there?
Q7: what do i do from now on???

---

### Post by Bashing-om on 2014-01-08
charitosha; Hey,

I will try and answer your questions,
1. MBR (Master Boot Record) is not a part of /boot. MBR is a reserved sector at the start of the hard drive that contains explicit code to locate and boot the operating system. This is where bios hands off to once bios' job is completed.

2.Nope, that position is pre-defined. It is a known location/address for all operating systems, the only variant is the code contained at this location.

3.tldp reference is that, this reference is but the minimum required. Mine:
```

sysop@1310mini:~$ sudo ls -la /
total 88
drwxr-xr-x  22 root root  4096 Jan  4 17:17 .
drwxr-xr-x  22 root root  4096 Jan  4 17:17 ..
drwxr-xr-x   2 root root  4096 Dec 22 10:23 bin
drwxr-xr-x   3 root root  4096 Jan  4 17:17 boot
drwxr-xr-x  15 root root  4340 Jan  8 10:55 dev
drwxr-xr-x  95 root root  4096 Jan  8 13:49 etc
-rw-r--r--   1 root root     0 Jul 18 11:30 forcefsdk
drwxr-xr-x   4 root root  4096 May 19  2013 home
lrwxrwxrwx   1 root root    33 Jan  4 17:17 initrd.img -> boot/initrd.img-3.11.0-15-generic
lrwxrwxrwx   1 root root    34 Jan  4 17:17 initrd.img.old -> /boot/initrd.img-3.11.0-15-generic
drwxr-xr-x  21 root root  4096 Dec 22 10:23 lib
drwxr-xr-x   2 root root  4096 Dec 22 10:19 lib64
drwx------   2 root root 16384 May 19  2013 lost+found
drwxr-xr-x   3 root root  4096 May 19  2013 media
drwxr-xr-x   6 root root  4096 Sep 15 10:35 mnt
drwxr-xr-x   3 root root  4096 May 19  2013 opt
dr-xr-xr-x 158 root root     0 Jan  8 10:54 proc
drwx------   7 root root  4096 May 20  2013 root
drwxr-xr-x  16 root root   540 Jan  8 10:59 run
drwxr-xr-x   2 root root 12288 Dec 22 10:23 sbin
drwxr-xr-x   2 root root  4096 May 19  2013 srv
dr-xr-xr-x  13 root root     0 Jan  8 10:54 sys
drwxrwxrwt   8 root root   240 Jan  8 18:17 tmp
drwxr-xr-x  10 root root  4096 May 19  2013 usr
drwxr-xr-x  12 root root  4096 Dec 22 09:49 var
lrwxrwxrwx   1 root root    30 Jan  4 17:17 vmlinuz -> boot/vmlinuz-3.11.0-15-generic
lrwxrwxrwx   1 root root    30 Jan  4 17:17 vmlinuz.old -> boot/vmlinuz-3.11.0-15-generic
sysop@1310mini:~$ 

```

4, No, init is a process (started by upstart as Process ID #1). initrd is:
> 
In computing, initrd is a scheme for loading a temporary root file system into memory in the boot process of the Linux kernel. initrd and initramfs refer to two different methods of achieving this. Both are commonly used to make preparations before the real root file system can be mounted.
[http://en.wikipedia.org/wiki/InitRD](http://en.wikipedia.org/wiki/InitRD)


5, Should not be empty ! Neither one ! .. If they are.. You most certainly have a) a bad burn to the install medium; b) a bad install to the hard drive.

6. Nope, should not be empty either, my response same same as my #5.

7. We keep struggelling on with our communications problems until we get you up and running ubuntu. What ever it takes.

Now once more, We need to get you able to boot with the liveDVD/USB or some install medium.

I want to know where you are seeing this "inramfs" prompt ? Is it from the liveUSB ? Or is the initramfs prompt from trying to boot into the actual install on the hard drive ? And I say again that many people have problems making up an installUSB using unetbootn. Try a different method if we think a bad installMEDIUM may be at fault.

Do not make this any more difficult than it is. The easy way is to boot up the liveDVD/ or USB to the "try ububtu" mode. This is a fully usable operating system from which to look at the install and effect any needed repairs - If you are not able to boot to "try ubuntu" most likely you have made a bad install on that hard disk. With the liveMEDIUM is the ability to wipe out that bad install, and  again to install ubuntu.

It is necessary for my piece of mind that you boot to "try ubuntu" in your install medium (USB or whatever). All my logic begins at that foundation.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-01-09
charitosha; Hey,

Still hanging in there with you;

Does this link exactly describe what we are looking at ?
[http://www.thelinuxguy.nl/how-tos/how-to-fix-initramfs-stdin-error-0-can-not-mount-devloop-cdromcasperfilesystem-squashfs-linux/](http://www.thelinuxguy.nl/how-tos/how-to-fix-initramfs-stdin-error-0-can-not-mount-devloop-cdromcasperfilesystem-squashfs-linux/)

[INDENT][INDENT]look'n at ways and means
[/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-11
Beshing-om hello!
You won't believe what happened... (i actually had an improvement)
Let's first sum the thing a bit up. I have a hp Mini (no cd-rom)
So unetbootin in a 16gb USB 3

I) When choose the try install option the display just go black. However if arrow keys are pressed for a fraction of a second the loading install screen is shown. But never going beyond that.
II) When in the install ubuntu i get : ubi-language crashed. ubi-language failed exit code 1. Choose continue anyway. Preparing to install ubuntu-continue, Wireless-continue, and then i get : ubi-partman failed with exit code 10. more Info at /var/log/syslog.
At the very end i'm stuck at the Welcome! screen. (i guess that the instalation is not over.)
III)Check disk for defects: can't unmount cd/rom device or resource busy. Also errors found in 209 files...
IV) Test Memory.
It says Cannot load a ramdisk with an old kernel image.
boot:

Now in the interesting part!
V)The Default option. 
If chosen, it will go to a loading screen and then the display will become black and that's the end of it.
However.
If i choose it and press arrowkeys at that loading screen. It will go in an cmd-like enviroment. it will load fast some things, most noticable that i remember: can't unmount cd/rom device or resource.
 another: chmod  /root/usr/sbin-update-initramfs no such file or directory.
But it end up with this:
```
[54.054080] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 88995
[54.491543] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 88943
Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-52-lowlatency-pae i686)
* documentation:  http://help.ubuntu.com/
ubuntu-studio@ubuntu-studio:~$
 
```
So it looks like i'm in the Terminal! 
Q1: Is it possible to just add a boot flag to a partition that have win7 or the ubuntu_live?(both of them are in the same hdd)
Q2: does $ mean that i don't have administrator clearance?
Q3: why,why on earth, were the arrowkeys mandatory, in order to get there?
AnywayZZZz since i was there i thought that the best thing would be to type some commands that you told me earlier. So:
[FONT=Calibri][COLOR=#000000]
sudo parted -l
```
Ubuntu-studio@ubuntu-studio:~$ sudo parted -l
Sudo: /etc/sudoers.d/casper is mode 0644, should be 0440
Model: ATA Hitachi HTS72502 (scsi)
Disk /dev/sda: 250 GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number   Start        End             Size              Type                File system               Flags
1             1049KB     210MB        209MB       primary          ntfs
2             210MB     205GB          205GB        primary          ntfs
3             231GB      250GB          18.8GB       primary         fat32                           lba          (THIS IS THE MISTEKENLY BURNT UBUNTU_LIVE which was supposed to be in a USB)
 
Model: ADATA USB Flash Drive (scsi)
Disk/dev/sdb: 15.8gb
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
 
Number   Start        End             Size              Type                File system               Flags
1             65.5KB      15.8GB        15.8GB       primary          fat 32                         boot,lba

```

sudo fdisk -lu
```
Ubuntu-studio@ubuntu-studio:~$ sudo fdisk -lu
Sudo: /etc/sudoers.d/casper is mode 0644, should be 0440
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal):512 bytes/512 bytes
Disk identifier: 0xb1303c4b
 
Device          Boot      Start                End                 Blocks              Id      System
/dev/sda1                 2048                409599          203776              7     HPFS/NTFS/exFAT
/dev/sda2                 409600           400279551    199934976       7      HPFS/NTFS/exFAT
/dev/sda3                  451481600    488193807    18351104         c      W95 FAT32 (LBA)
 
Disk /dev/sdb: 15.8 GB, 15805186048 bytes
255 heads, 63 sectros/track, 1921 cylinders, total 30869504 sectors
Units = sectors of 1*512 = 512 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk Identifier: 0x00000000
 
Device          Boot      Start                End                 Blocks              Id      System
/dev/sdb1        *        128        30869503         15434688               c      W95 FAT32 (LBA)

```

[FONT=Calibri][COLOR=#000000]sudo parted /dev/sda unit s print
```
Ubuntu-studio@ubuntu-studio:~$ sudo parted /dev/sda unit s print
Sudo: /etc/sudoers.d/casper is mode 0644, should be 0440
Model: ATA Hitachi HTS72502 (scsi)
Disk /dev/sda: 488397168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Device        Start                End                     Size              File system       Flags
1                  2048s             409599s             407552s            primary
2              409600s         400279551s      399869952s         primary
3        451481600s        488183807s         36702208s       primary         lba
   
```

lsblk -f
```
[FONT=Calibri][COLOR=#000000]Ubuntu-studio@ubuntu-studio:~$ lsblk -f
NAME     FSTYPE  LABEL    MOUNTPOINT
 Loop0                                                    /rofs
Loop1
Sda
    Sda1
    Sda2
    Sda3                                                   /cdrom
Sdb
    Sdb1[/COLOR][/FONT]
```

[/COLOR][/FONT][/COLOR][/FONT][FONT=Calibri][COLOR=#000000][FONT=Calibri][COLOR=#000000]Waiting for your reply, sorry for the long message and for not using tables

Is it going to be possible to locate MRB now? For installing grub overthere as you said previously.

P.S. Almost forgot!
From a link that you sent me i found [http://www.thelinuxguy.nl/how-tos/how-to-prepare-a-usb-stick-for-unetbootin-linux/](http://www.thelinuxguy.nl/how-tos/how-to-prepare-a-usb-stick-for-unetbootin-linux/) interesting. Thought why not try and so i was prepared to format an SD-Card (32 GB) but i had some differences (his 1st sector is 2048 mine 0), didn't know much so i played it safe and quited... 





[/COLOR][/FONT][/COLOR][/FONT]

---

### Post by Bashing-om on 2014-01-11
charitosha; I am so confused !

I do not have a clue what you are doing, in spite of all the "hints".

Back up and tell me explicitly what you are attempting to do.
1stly on the hard drive install, ubuntu MUST be installed onto a partition of file type "ext4".. not a Windows type as in NTFS or FAT32 !
My mind can only cope well with ONE item at a time. What is your primary ? ONE.

OK, in answer to your questions:
1. Yes, most likely a graphics problem; if you have Nvidia or ATI for graphics -> try boot parameter "nomodeset".
2.the '$' at the prompt is that you are at a terminal and have "user" access. This is the normal CLI prompt.
3. Pressing any key should have the same result, though the kernel is programmed to recognize  particular key strokes or sequences. Any keyboard activity "Might" be interpreted as an interrupt signal in the boot order and redirect the boot sequence to a terminal.

Change in direction: IF you are attempting to install ubuntu onto a USB thumb drive then yes, file system type fat32 is acceptable. However, I have never used unetbootn and I have no direct knowledge in it's use. Nor, have I ever installed onto a fat32 file system. Ubuntu's base/default is ext4
(though many others are supported).

Now, If it is your goal to install ubuntu onto the hard drive as a "proper" dual boot, Then, as sda is erroneously (sda3 ??) set up. I suggest that you use the Windows' disk utility to remove that partition -> unallocated space. In ubuntu installation, choose the option "something else" to allow you to choose to install ubuntu onto that unallocated space. The installer will take care of formatting and setting up the install, if a simple install is acceptable to you.

The base of all this is to KNOW that the install medium is sound. One must be able to boot the installmedium to "try ubuntu" mode, and as well that medium must pass "check disk for defects" testing. Until such time that you are able to boot to "try ubuntu" there is no point in doing anything at all else. All efforts will be directed to booting that installmedium. Whatever it may take to boot the installmedium to "try ubuntu" will be applicable to the actual install.

[INDENT][INDENT]cheerfully moving forward
[/INDENT][/INDENT]

---

### Post by charitosha on 2014-01-12
Bashing-om, awesomeness is on the way!!! :grin:

i guess my previous reply was a biiiit to big.
Anywayzzzzz great news i have installed successfully ubuntu!
while i was in the Terminal i deleted a partition and bam! instalation complete!

i want to show you where i choose  between win7 and ubuntu
```
GNU GRUB version1.99-21ubuntu3.10
Ubuntu, with Linux 3.2.0-52-lowlayency-pae
Ubuntu, with Linux 3.2.0-52-lowlayency-pae(recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, Serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)

```
Q1:why there are 2 Windows 7? if the 1st one is chosen then it will boot to the Windows OS, if the second one is chosen i get: ```
Windows Boot Manager
Windows failed to start. A recent hardware or Software change might be the cause. To fix the problem:
1.Insert your Windows installation disk and restart your computer.
2.Choose your language settingsn and then click "Next".
3.Click "repair your computer".

If you do not have this disc, contact your system administrator or computer monufacturer for Assistance.

Status: 0x000000f
Info: The boot selection failed because a required device is inaccessible.

Enter=continue                         ESC=Exit

```
so what's up with this Windows 7 (loader) (on /dev/sda2) partition? can i just delete it?

Q2: what's up with the memtest partition? why it's there?

---

### Post by Bashing-om on 2014-01-12
charitosha; Wonderfull !

Very pleased you are up and running ! .. Welcome to our world !

why there are 2 Windows 7? -> grub sees 2 partitions with boot code and does not know which is real, Windows requires both of them and as such MUST not be deleted... Leave well enough alone.

Q2: what's up with the memtest partition? why it's there? -> This is not a partition at all, but an application to test ones onboard memory (ram) . Believe me, it has it uses and applications when trouble shooting a hardware related problem.

OK, Now that you are up, the 1st thing (I hope you have already did this) is to update all the installed software to what is now current:
```

sudo apt-get update ##this syncs the databases between your system and that of the mirror site
sudo apt-get upgrade ## updates all your installed software to what is current on the mirror site

```
(the GUI application Ubuntu Software Center will also perform this function, but I prefer the terminal means to see all the action taking place)

By all means enjoy ubuntu -> the greatest operating system the world has ever known .

[INDENT][INDENT]there are solutions;
[INDENT][INDENT][INDENT]it is open source !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

