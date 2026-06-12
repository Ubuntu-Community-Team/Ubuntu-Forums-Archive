---
title: "Can't shutdown after trying out Live USB"
date: 2016-03-20
forum: General Help
---

### Post by vasa1 on 2016-03-20
I have a problem with a Lubuntu 16.04 Live USB.

My laptop is a Dell 1545 N Inspiron from 2009 --- USB 2, integrated graphics, Intel Core2Duo, 4GB RAM, 64-bit currently running Lubuntu 14.04 without any problem.

I download the iso from here: [http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/daily-live/current/xenial-desktop-amd64.iso)

I keep it updated using zsync.

I use mkusb to make the Live USB each time:
```
apt-cache policy mkusb
mkusb:
  Installed: 10.5.1-1ubuntu1
  Candidate: 10.5.1-1ubuntu1
  Version table:
 *** 10.5.1-1ubuntu1 0
        500 http://ppa.launchpad.net/mkusb/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```The latest mkusb log looks like this:
```
The mkusb console window displays,
or the file ~/mkusb.log contains:
output from the engine behind the zenity curtain.
---------------------------------------------------------------------------
start [mkusb 10.5.1] @ 2016-03-19 05:07:08  IST
---------------------------------------------------------------------------
Current directory=/home/vasa1
main: usbonly=true
main: liveonly=true
No input file specified yet
main: source=''
TERM=unknown
ubuntu
---------------------------------------------------------------------------
menu_shell:
imagefile=/home/vasa1/ZSYNC/xenial-desktop-amd64.iso
The iso file SHOULD BE loop mounted on a temporary file READ-ONLY:
mount: block device /home/vasa1/ZSYNC/xenial-desktop-amd64.iso is write-protected, mounting read-only
disk_name_type=desktop
Lubuntu 16.04 LTS "Xenial Xerus" - Alpha amd64 _found_ in iso-file
Lubuntu 16.04 LTS "Xenial Xerus" - Alpha amd64 _found_ in /dev/sdb
---------------------------------------------------------------------------
do_n_show:
pv -n "xenial-desktop-amd64.iso"| dd of="/dev/sdb" bs=4096
 
( pv -n "xenial-desktop-amd64.iso"| dd of="/dev/sdb" bs=4096 && echo 'Done' > /dev/stderr ) 2>&1 || ( echo '# failed';sleep 1 )
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
'pv %'; 'dd final output'
6
12
18
...
98
99
99
99
100
221440+0 records in
221440+0 records out
907018240 bytes (907 MB) copied, 161.746 s, 5.6 MB/s
Done
do_n_show: Work done
---------------------------------------------------------------------------
syncing the drive ...
The Lubuntu 16.04 LTS "Xenial Xerus" - Alpha amd64 USB device is updated  :-)
---------------------------------------------------------------------------
menu_shell:
Cleanup after mkusb finished :-)
---------------------------------------------------------------------------
Total time used [by mkusb] = 299 s; 00:04:59
login attempt 1
```The problem:
Each time I make a Live USB everything works just fine but when I choose to shutdown (or logout and then shutdown), I get a blank screen with a blinking cursor in the top left corner if I don't turn off the network connection and the laptop doesn't shutdown
or
I get a blank screen without the blinking cursor in the top left corner if I turn off the network connection before attempting shutting down and the laptop doesn't shutdown.

Even if I wait for a few minutes, nothing happens. The USB light remains on and my laptop doesn't power down.

I then have to long press the power button to shutdown my laptop.

I thought my issue was related to [http://ubuntuforums.org/showthread.php?t=2312728](http://ubuntuforums.org/showthread.php?t=2312728) but testers there say their problem has gone away. Mine remains. One difference maybe that they've done a full install whereas I'm using a live USB.

---

### Post by sudodus on 2016-03-25
This is a long-lived bug. I have read that it is caused by a race condition. See [this bug report,  #1447038](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1447038).

There are several duplicate bug reports:

    Bug #1508257
    Bug #1509923
    Bug #1510911
    Bug #1524405
    Bug #1531251
    Bug #1558481

so you can see that you are not alone. It affects systems in real computers as well as virtual machines. Sometimes but not always I am affected too, when I test Lubuntu Xenial.

It appears sometimes, and hides sometimes. I suggest that you avoid hard shutdown (pressing the power button for a long time). Instead I recommend

[SIZE=3]***SysRq + r e i s u b***[/SIZE]

The hotkey combination for ***SysRq*** is often but not always ***alt + PrtScrn***.

Keep the hotkey combination for SysRq pressed, and press slowly each of the keys ***r e i s u b*** one after another. See this link for more information about the method

[Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by vasa1 on 2016-03-25
> **sudodus said:**
> This is a long-lived bug. I have read that it is caused by a race condition. See [this bug report,  #1447038](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1447038).

...
...
...

 Instead I recommend

[SIZE=3]***SysRq + r e i s u b***[/SIZE]

The hotkey combination for ***SysRq*** is often but not always ***alt + PrtScrn***.

Keep the hotkey combination for SysRq pressed, and press slowly each of the keys ***r e i s u b*** one after another. See this link for more information about the method

[Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

Sudodus, thank you very much for the above information. I didn't want to push this matter because I thought I was *just me* and the rest of you are busy actively testing 16.04.

I should mention that I tried making a Live USB with unetbootin on at least two different daily images and there the shutdown was normal. 

```
06:30 PM ~ $ apt-cache policy unetbootin
unetbootin:
  Installed: 585-2ubuntu1
  Candidate: 585-2ubuntu1
  Version table:
 *** 585-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
06:30 PM ~ $ 
```

I then made another Live USB using mksub with the same daily images and again ran into the problem.

I know I've not done this enough to make it statistically significant but I just thought I'd mention it.

---

### Post by sudodus on 2016-03-25
The cloning method used by mkusb, gnome-disks and dd is used by the revamped Ubuntu Startup Disk Creator too in 16.04 LTS. Due to the cloning method the USB boot drive will be exactly the same using these tools.

And it should work without issues to shutdown and reboot, so I hope this bug will finally be squashed.

---

### Post by C.S.Cameron on 2016-03-25
I have noticed the shut down problem when adding a new user to a persistent install.
I have tried but not succeeded to create a desktop icon to do the shutdown.

[http://askubuntu.com/questions/582675/shutdown-persistent-usb-install](http://askubuntu.com/questions/582675/shutdown-persistent-usb-install)

---

### Post by sudodus on 2016-03-25
> **C.S.Cameron said:**
> I have noticed the shut down problem when adding a new user to a persistent install.
I have tried but not succeeded to create a desktop icon to do the shutdown.

[http://askubuntu.com/questions/582675/shutdown-persistent-usb-install](http://askubuntu.com/questions/582675/shutdown-persistent-usb-install)

Have you tried this one (borrowed from ToriOS live)?

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Shutdown
Exec=shutdown -h now
Icon=system-shutdown
Terminal=false
StartupNotify=false
```

You may need to find and specify your own icon.

---

### Post by sudodus on 2016-03-27
Hi vasa1,

I did some testing today with Lubuntu Xenial i386, and it seems that live systems booted from cloned drives do not shutdown correctly, but grub-n-iso systems are not affected by this bug. So a persistent live drive made with mkusb is not affected.

[See this link to the current bug report #1552985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985)
[and to my comment, #17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985/comments/17)

---

### Post by vasa1 on 2016-03-27
> **sudodus said:**
> Hi vasa1,

I did some testing today with Lubuntu Xenial i386, and it seems that live systems booted from cloned drives do not shutdown correctly, but grub-n-iso systems are not affected by this bug. **So a persistent live drive made with mkusb is not affected**.

[See this link to the current bug report #1552985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985)
[and to my comment, #17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985/comments/17)

Thank you, Sudodus! 

So if I make a ***persistent live drive*** using mkusb 10.5.1, will I be able to shut down properly? My USB stick is 8GB so I think I have the space.

*(I don't want to go the grub-n-iso route because that seems very complicated to me.)*

And if I do take the persistent live drive route, will I then just have to keep running *sudo apt-get update* and *sudo apt-get dist-upgrade* to keep it up to date instead of using zync on an iso and then making a live USB out of that?

In any case, when 16.04 is released I'll do a clean torrent download of that and use it to install 16.04.

*NOTE: I know how busy you are contributing to the success of 16.04 and I won't feel bad if you don't reply promptly!*

PS: My laptop is Dell Inspiron 1545 Core2Duo 64-bit, 4GB RAM with BIOS and no UEFI concerns.

---

### Post by sudodus on 2016-03-27
> **vasa1 said:**
> Thank you, Sudodus! 

So if I make a ***persistent live drive*** using mkusb 10.5.1, will I be able to shut down properly? My USB stick is 8GB so I think I have the space.
Yes, that's how it works for me :-)> 
*(I don't want to go the grub-n-iso route because that seems very complicated to me.)*

And if I do take the persistent live drive route, will I then just have to keep running *sudo apt-get update* and *sudo apt-get dist-upgrade* to keep it up to date instead of using zync on an iso and then making a live USB out of that?

In any case, when 16.04 is released I'll do a clean torrent download of that and use it to install 16.04.

*NOTE: I know how busy you are contributing to the success of 16.04 and I won't feel bad if you don't reply promptly!*

It is a good idea to use persistence to add functionality by installing packages and tweak the system to what you like, but it is ***not*** a good idea to update/upgrade a persistent live system continuously. Then you will soon get a borked system. It is better to continue zsyncing your iso file and make fresh live-only or persistent live systems with mkusb.

You can keep your tweaks as a backup of your casper-rw partition to another drive and restore it after upgrading your pendrive.

-o-

Another alternative is to use the system described in the following link and update the iso file(s) with rsync in situ (in the pendrive). Then you need mkusb 'only once'.

[A compressed image file with a persistent live system of Lubuntu 14.04.3 LTS (32-bit) and mkusb version 10.4](http://ubuntuforums.org/showthread.php?t=2259682&page=3&p=13399888#post13399888)

But during the development of the new version (now Xenial) things will happen, that can create conflicts between what is stored in the casper-rw partition and the new version of the daily iso file. So even in this case you may need to start all over again. Maybe you can keep the home directory (and wipe all other subdirectories of your overlay system in the casper-rw partition. Wipe while running it live-only.)

The Xenial system is stored in **/media/lubuntu/casper-rw/[COLOR="#0000FF"]upper[/COLOR]**

---

### Post by vasa1 on 2016-03-27
I went ahead and made a persistent USB :)
Here's the log:```
The mkusb console window displays,
or the file ~/mkusb.log contains:
output from the engine behind the zenity curtain.
---------------------------------------------------------------------------
start [mkusb 10.5.1] @ 2016-03-27 05:59:28  IST
---------------------------------------------------------------------------
Current directory=/home/vasa1
main: usbonly=true
main: liveonly=true
No input file specified yet
main: source=''
TERM=unknown
ubuntu
---------------------------------------------------------------------------
menu_shell:
---------------------------------------------------------------------------
menu_shell:
imagefile=/home/vasa1/ZSYNC/xenial-desktop-amd64.iso
Booted from: /dev/sda
ans=1
mount: block device /home/vasa1/ZSYNC/xenial-desktop-amd64.iso is write-protected, mounting read-only
[1;7m Lubuntu 16.04 LTS "Xenial Xerus" - Beta amd64 [0m
mount: block device /home/vasa1/ZSYNC/xenial-desktop-amd64.iso is write-protected, mounting read-only
'/home/vasa1/ZSYNC/xenial-desktop-amd64.iso' is identified as the source ISO file
<pre>
MODEL            NAME   FSTYPE LABEL       MOUNTPOINT   SIZE
Transcend 8GB    sdb                                    7.6G
                 &#9492;&#9472;sdb1 vfat   TRANSCENDLU              7.6G
</pre>
Using the file '/usr/share/mkusb/grub.cfg'
Using the file '/usr/share/mkusb/usb-pack_efi.tar.gz'
Clean for a GUID partition table
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): This option deletes all partitions and creates a new protective MBR.
Proceed? (Y/N): 
Command (? for help): 
Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): OK; writing new GUID partition table (GPT) to /dev/sdb.
The operation has completed successfully.
Wipe the first megabyte (mibibyte) to get a clean boot area
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.281032 s, 3.7 MB/s
---------------------------------------------------------------------------
Selected percentage of remaining space for persistence = 80
---------------------------------------------------------------------------
 
preparing /dev/sdb3  ------------------------------------------------
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 0.279597 s, 3.8 MB/s
mkfs.fat 3.0.26 (2014-03-07)
/dev/sdb3 has 250 heads and 62 sectors per track,
hidden sectors 0x1000;
logical sector size is 512,
using 0xf8 media descriptor, with 249856 sectors;
drive number 0x80;
filesystem has 2 32-bit FATs and 1 sector per cluster.
FAT size is 1922 sectors, and provides 245980 clusters.
There are 32 reserved sectors.
Volume ID is 2ae4f133, no volume label.
 
preparing /dev/sdb1  ------------------------------------------------
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 1.51727 s, 691 kB/s
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.
preparing /dev/sdb5  ------------------------------------------------
1024+0 records in
1024+0 records out
1048576 bytes (1.0 MB) copied, 1.39136 s, 754 kB/s
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
340032 inodes, 1359104 blocks
67955 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1392508928
42 block groups
32768 blocks per group, 32768 fragments per group
8096 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Allocating group tables:  0/42     done                            
Writing inode tables:  0/42     done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information:  0/42     done

mount: according to mtab /home/vasa1/ZSYNC/xenial-desktop-amd64.iso is already mounted on /tmp/tmp.2FX1hUW6Ka as loop
tune2fs 1.42.9 (4-Feb-2014)
---------------------------------------------------------------------------
source=/home/vasa1/ZSYNC/xenial-desktop-amd64.iso
---------------------------------------------------------------------------
mount /dev/sdb3 /tmp/tmp.epTODq17k7
/dev/sdb3       121M   512  121M   1% /tmp/tmp.epTODq17k7
UEFI Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
BIOS Bootloader:  Installing for i386-pc platform.
Installation finished. No error reported.
using usb-pack_efi.tar.gz
./
./boot/
./boot/grub/
./boot/memtest/
./boot/memtest/memtest86+-5.01.bin
./boot/memtest/memtest.bin
./EFI/
./EFI/BOOT/
./EFI/BOOT/bootx64.efi
./EFI/BOOT/bootia32.efi
---------------------------------------------------------------------------
do_n_show:
&lt; "/home/vasa1/ZSYNC/xenial-desktop-amd64.iso" pv -n | dd of=/dev/sdb4 bs=4096
 
( < "/home/vasa1/ZSYNC/xenial-desktop-amd64.iso" pv -n | dd of=/dev/sdb4 bs=4096 && echo 'Done' > /dev/stderr ) 2>&1 || ( echo '# failed';sleep 1 )
Please wait for sync (flushing file system buffers to the device)
until 'Done' is written ...
'pv %'; 'dd final output'
6
13
... lines deleted by me
98
99
99
100
241408+0 records in
241408+0 records out
988807168 bytes (989 MB) copied, 180.866 s, 5.5 MB/s
Done
do_n_show: Work done
---------------------------------------------------------------------------
Syncing the target device ...
<pre>
parted -s "/dev/sdb" print
Model: JetFlash Transcend 8GB (scsi)
Disk /dev/sdb: 8097MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 2      1049kB  2097kB  1049kB               primary  bios_grub
 3      2097kB  130MB   128MB   fat32        primary  boot
 4      130MB   1138MB  1008MB               primary
 5      1138MB  6705MB  5567MB  ext4         primary
 1      6705MB  8096MB  1391MB  ntfs         primary  msftdata

lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE "/dev/sdb"
MODEL            NAME   FSTYPE  LABEL                   MOUNTPOINT   SIZE
Transcend 8GB    sdb                                                 7.6G
                 &#9500;&#9472;sdb1 ntfs    usbdata                              1.3G
                 &#9500;&#9472;sdb2                                                1M
                 &#9500;&#9472;sdb3 vfat    xenial64                             122M
                 &#9500;&#9472;sdb4 iso9660 Lubuntu 16.04 LTS amd64              961M
                 &#9492;&#9472;sdb5 ext4    casper-rw                            5.2G
</pre>
Done :-)
The target device is ready to use.
'/home/vasa1/ZSYNC/xenial-desktop-amd64.iso' was installed
Cleanup after mkusb finished :-)
Zenity error log-file 'zerrlog'=/tmp/tmp.BSS1bf7Ub1
---------------------------------------------------------------------------
menu_shell:
Cleanup after mkusb finished :-)
---------------------------------------------------------------------------
Total time used [by mkusb] = 428 s; 00:07:08
login attempt 1

```

I take your point about not expecting the persistent USB to keep going perfectly. Thanks for the caution!

---

### Post by sudodus on 2016-03-27
The log file looks good. Let me know how it works in your computer :-)

---

### Post by vasa1 on 2016-03-27
I'm using it right now :)

Bit slower I'm guessing because of all the writing to the pendrive (USB 2).

---

### Post by sudodus on 2016-03-27
Yes, a persistent live system is slower than a live-only system, particularly during boot.

Please describe the behaviour at shutdown of

- the cloned live-only system and
- the persistent live system 

(including what computer you are running) in the [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985).

---

### Post by vasa1 on 2016-03-27
> **sudodus said:**
> Yes, a persistent live system is slower than a live-only system, particularly during boot.

Please describe the behaviour at shutdown of

- the cloned live-only system and
- the persistent live system 

(including what computer you are running) in the [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1552985).
**The shutdown of the persistent live usb was without problems!** And so I'll mark this thread [SOLVED]. If you want me to leave it as unsolved, please let me know and I'll reverse it.

I will post in the bug tomorrow. By "the cloned live-only system", do you mean what I reported in this thread earlier?

---

### Post by sudodus on 2016-03-27
It is fine to mark this thread [SOLVED] :-)

And yes, by "the cloned live-only system", I mean what you reported in this thread earlier.

---

