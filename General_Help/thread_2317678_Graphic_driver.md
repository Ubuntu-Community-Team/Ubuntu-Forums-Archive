---
title: "Graphic driver"
date: 2016-03-18
forum: General Help
---

### Post by mac-2check on 2016-03-18
Hello,

We have at home an old pc which had W7 and was still quite fast, but then I put there xubuntu and the pc got really slow, which was strange because xubuntu is much less demanding then W7, but I didnt care about it much back then, later on the main graphic card got broken and I switched to the integrated one and the pc got even slower and I had to use the resolution 1024x800 on 22 lcd, which was annoying so I was googling how to change the resolution and got the idea that I didn't have a proper graphic driver, so I went to settings and found out that I was using an open source driver. I switched to a n-vidia driver which was on the list, waited about 10 mins, then rebooted as requested, and now when I turn the pc on the only thing which appears on the screen is blinking _

I think I need to switch back to the previous open sourse driver and then get the right driver.  I can boot a xubuntu live cd, and then somehow in terminal change it, but I have no idea how to do it, so I would like to ask you for help.


Thanks in advance,

Martin

---

### Post by Bashing-om on 2016-03-18
mac-2check; Hello;

Now that just is not right. xubuntu should fly if Windows7 flew.
Lets look at the hardware, drivers, and what X is doing.
At the login screen key combo ctl+alt+F1 yields a console interface.
Install our pastebin tool, so you do not have to do all the typing:
```

sudo apt install pastebinit

```

And now relay:
```

lspci -k | grep -EA2 'VGA|3D' | pastebinit
sudo lshw -C | pastebinit
pastebinit /var/log/Xorg.0.log

```
The results are URLs back in terminal, pass these links back here . We access the files and get an idea of what is not taking place.

[INDENT][INDENT]cause and effect
[INDENT][INDENT][INDENT]in all things
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-18
Hello Bashing-om, thanks for helping.

here is the link: [http://paste.ubuntu.com/15417722](http://paste.ubuntu.com/15417722).

right now Im trying to repair it through boot-repair live cd, so hopefully I will succeed.....

---

### Post by Bashing-om on 2016-03-18
mac-2check; Huh ??


This :
> 
Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash -- persistent BOOT_IMAGE=/casper/vmlinuz.efi 
[   136.738] Build Date: 16 April 2014  01:36:29PM

indicates to me that this log file is from the liveDVD(USB).

We do want to be able to work from the install.

See: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
for guidance to install on a EFI system.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-18
I cannot run the system, while booting it is just endlessly loading, so I thought I would run a live cd and got the log you need from there...

---

### Post by Bashing-om on 2016-03-18
mac-2check; Yuk ..

OK, a log file from the live environment depicts what is going on in this live environment. We needed to know about the install.

As you can not boot the install at all that indicates :
a) a bad install medium .. did you verify the integrity of the downloaded .iso file ? and did you verify the copy to medium ?
b) A EFI install attempt, and no provision made for the EFI /boot partition ?

From that live environment, show us what we are working with;
post back - between code tags:
```

sudo parted -l
sudo blkid -c /dev/null

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And away we go again;
[INDENT][INDENT]point to the why not
[/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-18
I installed it a month ago and everything was alright, expect the immense slowness, then I had to switch to another graphic card and wanted to change the resolution by using a nvidia driver, instead of the open source one. And now I cannot boot the system.

here is the first command, the other doesnt work :confused:
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA ST3320620AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Model: ATA ST3160811AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  31.8GB  31.8GB  primary   ext4            boot
 2      31.8GB  109GB   77.0GB  extended                  lba
 5      31.8GB  109GB   77.0GB  logical   ntfs
 3      109GB   159GB   49.7GB  primary   ext4
 4      159GB   160GB   1505MB  primary   linux-swap(v1)


Model: SCSI SG 1.8.1.7.0 2+6 (scsi)
Disk /dev/sdc: 8069MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      24.6kB  8069MB  8069MB  primary  fat32        boot


Error: /dev/zram0: unrecognised disk label

---

### Post by Bashing-om on 2016-03-18
mac-2check; OK;

We are looking at a legacy install so EFI is not a factor.

As you say the system was bootable, and all you have done is change the graphic's hardware; then there "should' be no reason why you can not boot to grub or boot to a terminal.

Let's see what results in booting to a terminal:
reboot the install .... ubuntu is installed to the 2nd hard drive, and boot code is installed to this 2nd hard drive. so in bios make sure that the 2nd hard drive is selected as 1st boot priority.
When now booting, do you boot to the grub boot menu ?

If you reach the grub boot menu .. select the newest 'buntu kernel to boot, and press the 'e' key for edit mode -> boot parameters screen;
arrow down to the line starting with linux. and arrow across to "quiet splash" replace these terms with the term "text" - without the quotes. key combo ctl+x to continue the boot process to TTY1.
At the TTY1 terminal log into the system with your username and password . There will be no response to the screen when password is entered. Enter your pass word blindly and hot the enter key.

Now, once at a terminal .. we can look at the graphics situation and make reconciliation . If you can not get to a terminal... there are other factors at play here than that of the graphic's driver. At this point - booting to terminal - the GUI driver is not a factor.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-18
I've done as said, but got stuck, look at the pics. I guess I made a mistake somewhere.

the second picture is what happened when I pressed ctrl + x

---

### Post by Bashing-om on 2016-03-18
mac-2check; Ouch !

That do say that as directed grub can not find it's config files.

Let's take a stab at booting this system ... before we  resort to (RE-)installing grub .
The boot-repair utility will do this .. but as this is a multi disk system system .. care and caution is to be exercised. Maybe a bit beyond the less experienced user. If indeed this is a grub-config issue .

As the booting kernel is of the 4.2 series .. I must ask again .. what release is this ? As if 14.04 ( running with HWE) then the startup is of the upstart system ;
IF 15.10 then it is systemd as that startup system . How we get to a terminal is different in the respective releases.


A case of apples and oranges

---

### Post by mac-2check on 2016-03-18
I installed xubuntu-15.10-desktop-amd64

ps: I'm going to sleep, its a bit late here in the Czech rep.
thanks for your help so far, I'll continue tomorrow :)

---

### Post by Bashing-om on 2016-03-18
mac-2check; OK;


15.10 ! In a new light .
Instead of the 'text' boot parameter, make that " systemd.unit=multi-user.target " and also remove "$vt_handoff" .

When you are back, and logged into terminal we pick this back up and find out what is not going on .

[INDENT][INDENT]all in the right process
[/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-19
Good morning,

I changed it, but got the same error, maybe I wrote it wrong, see the pics

---

### Post by Bashing-om on 2016-03-19
mac-2check; Yuk ...

A couple of considerations now.
1) File system corruption, do we need to run a file system check/repair ?
2) Boot config files are in dis-array, do we re-install the boot code ?

let's get a bit more info.
Boot the liveUSB to a terminal:

post back:
```

sudo fdisk -lu
sudo blkid

```
and we look at what we have to work toward .

[INDENT][INDENT]now it is a thing
[/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-19
# sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e47b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007f33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    62138766    31068359+  83  Linux
/dev/sdb2        62139481   212539949    75200234+   f  W95 Ext'd (LBA)
/dev/sdb3       212539950   309636809    48548430   83  Linux
/dev/sdb4       309636810   312576704     1469947+  82  Linux swap / Solaris
/dev/sdb5        62139483   212539949    75200233+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 16.1 GB, 16131293184 bytes
64 heads, 32 sectors/track, 15384 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31506431    15753200    c  W95 FAT32 (LBA)
# 


# sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="disk-3" UUID="1990E4522AD9383F" TYPE="ntfs"
/dev/sdb1: UUID="ba87e5d1-6d17-4191-98ee-f60f12fa7282" TYPE="ext4"
/dev/sdb3: UUID="effbe6c4-f4d0-4747-bbd7-833cc76b773a" TYPE="ext4"
/dev/sdb4: UUID="abd085cc-4747-478f-80a6-77e50d3f6e30" TYPE="swap"
/dev/sdb5: UUID="1287810EBCB5E311" TYPE="ntfs"
/dev/sdc1: UUID="39E8-75C1" TYPE="vfat"
#

---

### Post by Bashing-om on 2016-03-19
mac-2check; Well,

So far so good . Let's find ubunu's root partition , then we check the files there.
We mount the target file system from the liveUSB and have a looksee:

```

sudo mkdir /mnt/looksee
sudo mount /dev/sdb1 /mnt/looksee
ls -al /mnt/looksee
ls -al /mnt/looksee/boot/

```

Expecting that you have set up sdb3 as your /home partition, thus we focus our attention to sdb1 .

To unmount what we have mounted, prior to rebooting, MUST do:
```

sudo umount /mnt/looksee

```

[INDENT][INDENT]progress made
[INDENT][INDENT][INDENT]small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-19
# ls -al /mnt/looksee
total 1880
drwxr-xr-x  24 root root    4096 Mar 19 04:23 .
drwxr-xr-x  13 root root      80 Mar 19 20:56 ..
drwxr-xr-x   2 root root    4096 Jan 20 21:16 bin
drwxr-xr-x   3 root root    4096 Mar 19 02:11 boot
drwxr-xr-x   2 root root    4096 Jan 20 20:51 cdrom
-rw-------   1 root root 1798144 Feb 28 02:29 core
drwxr-xr-x   5 root root    4096 Oct 21 23:55 dev
drwxr-xr-x 133 root root   12288 Mar 19 02:11 etc
drwxr-xr-x   3 root root    4096 Jan 20 20:53 home
lrwxrwxrwx   1 root root      32 Mar 19 02:05 initrd.img -> boot/initrd.img-4.2.0-27-generic
lrwxrwxrwx   1 root root      32 Jan 20 21:24 initrd.img.old -> boot/initrd.img-4.2.0-25-generic
drwxr-xr-x  25 root root    4096 Mar 19 02:07 lib
drwxr-xr-x   2 root root    4096 Mar 19 02:07 lib32
drwxr-xr-x   2 root root    4096 Oct 21 23:48 lib64
drwx------   2 root root   16384 Jan 20 20:42 lost+found
drwxr-xr-x   4 root root    4096 Jan 23 23:08 media
drwxr-xr-x   2 root root    4096 Oct 19 17:14 mnt
drwxr-xr-x   4 root root    4096 Jan 20 21:47 opt
drwxr-xr-x   2 root root    4096 Oct 19 17:14 proc
-rw-r--r--   1 root root       7 Mar 19 19:24 pupdesk.flg
drwx------   5 root root    4096 Jan 23 23:22 root
drwxr-xr-x  11 root root    4096 Oct 21 23:56 run
drwxr-xr-x   2 root root   12288 Jan 20 21:17 sbin
drwxr-xr-x   2 root root    4096 Oct 21 23:48 srv
drwxr-xr-x   2 root root    4096 Oct 16 17:30 sys
drwxrwxrwt   7 root root    4096 Mar 19 18:17 tmp
drwxr-xr-x  11 root root    4096 Mar 19 02:07 usr
drwxr-xr-x  13 root root    4096 Oct 21 23:59 var
lrwxrwxrwx   1 root root      29 Mar 19 02:05 vmlinuz -> boot/vmlinuz-4.2.0-27-generic
lrwxrwxrwx   1 root root      29 Jan 20 21:24 vmlinuz.old -> boot/vmlinuz-4.2.0-25-generic
# 
# 
# 
# 
# ls -al /mnt/looksee/boot/
total 112516
drwxr-xr-x  3 root root     4096 Mar 19 02:11 .
drwxr-xr-x 24 root root     4096 Mar 19 04:23 ..
-rw-r--r--  1 root root  1311978 Oct  9 01:15 abi-4.2.0-16-generic
-rw-r--r--  1 root root  1312266 Jan 18 22:05 abi-4.2.0-25-generic
-rw-r--r--  1 root root  1312378 Jan 22 15:02 abi-4.2.0-27-generic
-rw-r--r--  1 root root   184809 Oct  9 01:15 config-4.2.0-16-generic
-rw-r--r--  1 root root   184850 Jan 18 22:05 config-4.2.0-25-generic
-rw-r--r--  1 root root   184888 Jan 22 15:02 config-4.2.0-27-generic
drwxr-xr-x  5 root root     4096 Mar 19 05:02 grub
-rw-r--r--  1 root root 33822442 Jan 20 21:01 initrd.img-4.2.0-16-generic
-rw-r--r--  1 root root 33166012 Mar 19 02:08 initrd.img-4.2.0-25-generic
-rw-r--r--  1 root root 11489408 Mar 19 02:11 initrd.img-4.2.0-27-generic
-rw-r--r--  1 root root   182704 Aug 27  2015 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 27  2015 memtest86+.elf
-rw-r--r--  1 root root   184840 Aug 27  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3740437 Oct  9 01:15 System.map-4.2.0-16-generic
-rw-------  1 root root  3740849 Jan 18 22:05 System.map-4.2.0-25-generic
-rw-------  1 root root  3743953 Jan 22 15:02 System.map-4.2.0-27-generic
-rw-r--r--  1 root root  6797696 Jan 20 20:50 vmlinuz-4.2.0-16-generic
-rw-------  1 root root  6799888 Jan 18 22:05 vmlinuz-4.2.0-25-generic
-rw-------  1 root root  6805392 Jan 22 15:02 vmlinuz-4.2.0-27-generic
# 
#

---

### Post by Bashing-om on 2016-03-19
mac-2check; Ho Kay ..

We know what hard drive, what partition contains 'root'. and looks like the file system is intact.
Let's prepare to boot this install from grub.

Now I am not positive how grub will identify the file system.
Boot the install to grub's boot menu - 'c' key for a command line mode

grub command:
```

ls -lh (hd1,msdos1)/boot/grub/grub.cfg

```
return a positive result ?

else what about changing the hard drive identifier:
```

ls -lh (hd0,msdos1)/boot/grub/grub.cfg

```
because I sometimes see that grub assigns 'hd0' as the booting hard drive .

Once we know what is true. we tell grub where it's config files are, and grub will tell the kernel where the required files are located, we try and see what results when we boot the install from grub .. and IF boots in this simple manner, we rell grub to re-configure with the system booted up as is .

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-19
I ran the first command and nothing came back, so I think we got a positive result. The other command turned into: error: file grub.cfg not found

---

### Post by Bashing-om on 2016-03-19
mac-2check; Ouch //

Now I am a bit confused,

The "ls (hd1,msdos1)" command should have had as output something similar:
> 
-r--r--r-- 1 root root 47857 Mar 17 11:17 /boot/grub/grub.cfg

Until such time as we know the truth we can not direct grub in what to do.

And conversely, if that file does not exist - somewhere - we have a problem . ( but even then we can fix )

[INDENT][INDENT]we can not lie to grub
[INDENT][INDENT][INDENT]and have a booting system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-19
I tried again, and the file just doesnt exist :o

---

### Post by Bashing-om on 2016-03-19
mac-2check; Ho Kay ..

Then we do the something else, explicitly install grub to sdb .
Boot the liveUSB to terminal:
Make sure our target is still identified as 'sdb' - the identifier can change depending on what order a operating system recognizes devices.
we do in terminal:
```

sudo fdisk -lu

```
and confirm you see:
> 
Disk /dev/sdb: 160.0 GB,
/dev/sdb1 * 2048 62138766 31068359+ 83 Linux


Target confirmed, then in the liveUSB terminal run:
```

sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdb
sudo umount /mnt

```

reboot to bios and reset the boot priority to the 2nd hard drive ( sdb); 
and boot the install.

Once booted up in the install run terminal command:
```

sudo apt update
sudo apt upgrade
sudo update-grub

```
to pick up and chainload Windows onto grub's boot menu.

[INDENT][INDENT]workie great ?
[INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-20
bad news: the pc got broken, firstly I couldnt load nor xubuntu live cd nor puppy linux, then I tried to switch to the previous graphic card which should have been dead and miraculously the pc loaded the whole system, but the keyboard and mouse just don't work. The same happens when I loaded a live cd, and reinstalling doesnt work. So I think, its time to buy a new one. After all the pc is 12 years old...

Thanks for your help and time Bashing-om :)

---

### Post by Bashing-om on 2016-03-20
mac-2check; Ouch !

Maybe, only just a maybe .... give that box a good thorough cleaning, paying particular attention to the cooling fan in the power supply .
We can hope it is dust shorting out the circuitry. While opened up look for capacitors on the mainboard that are swollen or leaking.

Life without your best friend
[INDENT][INDENT][INDENT]will be a trial
[/INDENT][/INDENT][/INDENT]

---

### Post by mac-2check on 2016-03-21
well, I tried it and yesterday it worked a while, but then did not and today it again doesnt work. Its an old machine used mainly by my parents so I'd better get something that works reliably, as Im often not at home....

Once again thanks for your help ;)

---

### Post by Bashing-om on 2016-03-21
mac-2check; Uh Huh :

I can understand:
> 
 Its an old machine used mainly by my parents so I'd better get something that works reliably


Power supply failing  ??
when the box warms up capacitors leaking ?

It do point to hardware issues .

[INDENT][INDENT][INDENT]nothing last forever
[/INDENT][/INDENT][/INDENT]

---

