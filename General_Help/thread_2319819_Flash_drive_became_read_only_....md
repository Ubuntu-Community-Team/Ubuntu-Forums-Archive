---
title: "Flash drive became read only ..."
date: 2016-04-07
forum: General Help
---

### Post by Innernet on 2016-04-07
Years saving files on a thumb/flash drive; now does not allow to save.  Message is being 'read only'   Checking permissions, am supposed to be able to alter/modify/write.  Trying to change permissions, message is 'cannot change permissions'
_Nobody else_ uses my compfuser.  Always had full access to everything.  Something went wrong.
Tried another flash drive; same result. 

The only thing of suspicion is I took both flash drives to a CVS site to print pictures contained in the drives.  Now they behave as locked to save.

Tried a third drive that has never been at CVS : same 'read only' message.

What should I do to return to normal, step by step guidance for an idiot ?

---

### Post by sudodus on 2016-04-07
I think there are two possible causes of your problem.

0. In both cases I suggest that you ***backup*** all important files from your flash drive as soon as possible.

1. You have managed to damage the file system, but the pendrive itself (hardware and internal programming) is still healthy.

2. The drive is failing, and is 'gridlocked' which is the first stage. The next stage is that it is completely dead.

See these links (and links from them)

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by Innernet on 2016-04-07
Adding stuff, and...  WTF has a Windows item to do here ?  (lower right message)

[ATTACH=CONFIG]268227[/ATTACH]
[ATTACH=CONFIG]268228[/ATTACH]

---

### Post by sudodus on 2016-04-07
I don't know. But I suggest that you do it the safe way and start with a backup.

Then you can look more into the problem. I suppose that you have been writing to these flash drives many times before, so something unusual has happened.

- Have you tried in another computer?

- Maybe try with some other operating system (a live Ubuntu system, free from possible damages, another linux distro live, or Windows)?

- Please post the output of the following commands, when the flash drives are connected, and check for the permissions

```
df
sudo lsblk -fm
ls -l /media
ls -l /media/$USER
```

It is possible that the mount point has no write permissions for your regular user. In that case it should be fairly easy to fix it.

---

### Post by mcduck on 2016-04-07
> **Innernet said:**
> 
The only thing of suspicion is I took both flash drives to a CVS site to print pictures contained in the drives.  Now they behave as locked to save.

If this happened after taking files to print shop with that drive, my guess would be the print shop people unplugged the drive without correctly removing it first, resulting the file system being marked as unclean. And that would cause Linux to mount the drive in read-only mode to prevent any further damage. If that's the case, then you should see a warning message explaining that in syslog when you plug the drive in.

If you have a Windows computer available, or can get to one, plug the drive in it, let Windows fix it's filesystem, and then remove the drive properly.

(what comes to changing permissions, that's not going to happen on any drive formatted using FAT, ExFAT or NTFS filesystems, as those don't support Unix-style permissions. Instead the permissions are set for the whole drive at the time it's mounted)

---

### Post by Innernet on 2016-04-07
Thanks, gentlemen.
Sudodus :

Per your instructions; myself cannot interpret the language.

================================================

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      150868180 8384684 134796740   6% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1411312       4   1411308   1% /dev
tmpfs             284188    1152    283036   1% /run
none                5120       0      5120   0% /run/lock
none             1420924     204   1420720   1% /run/shm
none              102400      36    102364   1% /run/user
/dev/sdb1         984784   32784    952000   4% /media/externet/7C9F-4968
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ sudo lsblk -fm
[sudo] password for externet: 
NAME   FSTYPE LABEL MOUNTPOINT                NAME     SIZE OWNER GROUP MODE
sda                                           sda    149.1G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /                         &#9500;&#9472;sda1 146.3G root  disk  brw-rw----
&#9500;&#9472;sda2                                        &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap         [SWAP]                    &#9492;&#9472;sda5   2.8G root  disk  brw-rw----
sdb                                           sdb      962M root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat         /media/externet/7C9F-4968 &#9492;&#9472;sdb1   962M root  disk  brw-rw----
sr0                                           sr0     1024M root  cdrom brw-rw----
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /media
total 4
drwxr-x---+ 3 root root 4096 Apr  7 17:13 externet
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /media/$USER
total 16
drwx------ 7 externet externet 16384 Dec 31  1969 7C9F-4968
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ 

===================================================

Edited, added : On a Windows machine, I was able to save and read files. Removed drives properly and no change back on Ubuntu.  Cannot save and message "read only"

---

### Post by sudodus on 2016-04-08
> **Innernet said:**
> Thanks, gentlemen.
Sudodus :

Per your instructions; myself cannot interpret the language.

================================================

```
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      150868180 8384684 134796740   6% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1411312       4   1411308   1% /dev
tmpfs             284188    1152    283036   1% /run
none                5120       0      5120   0% /run/lock
none             1420924     204   1420720   1% /run/shm
none              102400      36    102364   1% /run/user
[COLOR="#0000FF"]/dev/sdb1         984784   32784    952000   4% /media/externet/7C9F-4968[/COLOR]

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ sudo lsblk -fm
[sudo] password for externet: 
NAME   FSTYPE LABEL MOUNTPOINT                NAME     SIZE OWNER GROUP MODE
sda                                           sda    149.1G root  disk  brw-rw----
&#9500;&#9472;sda1 ext4         /                         &#9500;&#9472;sda1 146.3G root  disk  brw-rw----
&#9500;&#9472;sda2                                        &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap         [SWAP]                    &#9492;&#9472;sda5   2.8G root  disk  brw-rw----
sdb                                           sdb      962M root  disk  brw-rw----
&#9492;&#9472;[COLOR="#0000FF"]sdb1 vfat         /media/externet/7C9F-4968 &#9492;&#9472;sdb1   962M root  disk  brw-rw----[/COLOR]
sr0                                           sr0     1024M root  cdrom brw-rw----

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /media
total 4
[COLOR="#0000FF"]drwxr-x---+ 3 root root 4096 Apr  7 17:13 externet[/COLOR]

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /media/$USER
total 16
[COLOR="#0000FF"]drwx------ 7 externet externet 16384 Dec 31  1969 7C9F-4968[/COLOR]

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ 
```

===================================================

Edited, added : On a Windows machine, I was able to save and read files. Removed drives properly and no change back on Ubuntu.  Cannot save and message "read only"

I put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read. Please do the same in the future: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually).

The superuser 'root' owns **/media/externet** and your own user ID 'externet' owns **/media/externet/7C9F-4968** and has read,write,execute permissions, and it should mean that you should be able to write files into it.

- What do you mean by 'save files': to you mean 'backup files from the flash drive to another drive' or 'write files to the flash drive'?

Please run also the following command line and post the output:

```
ls -l /media/$USER/*
```

If you still cannot write files to the flash drive, please try the following:

1. Run also the following command line and post the output:

```
ls -l /media/$USER/*
```

2. Unmount [the partition on] the flash drive

```
sudo umount /media/externet/7C9F-4968
```

3. Mount [the partition on] the flash drive manually

```
sudo mount /dev/sdb1 /mnt
```

4. Run the following command line and post the output:

```
ls -l /mnt/*
```

5. Try to write a file to the flash drive and check it

```
echo "Hello World" > /mnt/hello.txt
cat /mnt/hello.txt

```

I think you are not allowed to write like this.

6. Try with superuser privileges and check again

```
sudo bash -c 'echo "Hello Superuser World" > /mnt/hello.txt'
cat /mnt/hello.txt

```

If the pendrive is OK, you should be able to write with superuser privileges.

I suggest these tests in order to find out if the problem depends on the settings of write privileges or if it depends on some problem with the flash drive itself.

-o-

If you did not do it before, ***please check and repair the file system of the flash drive in Windows***, either via the graphical user interface or with the command line

```
chkdsk /f X:
``` where X: is the drive letter for the flash drive.

---

### Post by Innernet on 2016-04-08
]Sudodus :  Thanks for your **great** guidance :

-By save files I meant save into the flash drive (write to it).

[ATTACH=CONFIG]268238[/ATTACH]

[ATTACH=CONFIG]268239[/ATTACH]

At next step (unmount), the system does not recognize my password when requested by the terminal !  It has never been changed !  It has never done that before !  I will pause here until you guide me to fix that.

Edited:  Trying again, got to this:


================================================================

```
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /mnt/*
-rwxr-xr-x 1 root root 1445717 Oct  5  2012 /mnt/Maleki.pdf
-rwxr-xr-x 1 root root     505 Aug  1  1993 /mnt/PARK.COM
-r-xr-xr-x 1 root root      82 Apr 20  2014 /mnt/READ.ME
-rwxr-xr-x 1 root root   46312 Aug  1  1993 /mnt/SPININFO.EXE
-rwxr-xr-x 1 root root  185165 Aug  1  1993 /mnt/SPININFO.XDB
-r-xr-xr-x 1 root root   94876 Jan  2  1980 /mnt/SPINRIT2.ZIP
-r-xr-xr-x 1 root root  241289 Jan  2  1980 /mnt/SPINRIT3.ZIP
-rwxr-xr-x 1 root root   73810 Aug  1  1993 /mnt/SPINRITE.EXE
-rwxr-xr-x 1 root root  106421 Apr 26  2015 /mnt/Spinrite-II_V20.zip
-r-xr-xr-x 1 root root  101745 Jan 29  1993 /mnt/SPINRITE.ZIP
-rwxr-xr-x 1 root root   90233 Jan 26 21:12 /mnt/TDA7056A.pdf

/mnt/Cayman:
total 6400
-rwxr-xr-x 1 root root 2071751 Aug 30  2015 IMG_6820.JPG
-rwxr-xr-x 1 root root 2320995 Aug 30  2015 IMG_6821.JPG
-rwxr-xr-x 1 root root 2143755 Aug 30  2015 IMG_6822.JPG

/mnt/IBM 600E Win98:
total 16
drwxr-xr-x 8 root root 16384 Jul  7  2010 BIOS

/mnt/SpinRite 2:
total 304
-rwxr-xr-x 1 root root    505 Mar  1  1991 PARK.COM
-rwxr-xr-x 1 root root   1763 Mar  1  1991 README.NOW
-rwxr-xr-x 1 root root  36816 Mar  1  1991 SPININFO.EXE
-rwxr-xr-x 1 root root 174201 Mar  1  1991 SPININFO.H!
-rwxr-xr-x 1 root root  47473 Mar  1  1991 SPINRITE.COM

/mnt/Spinrite 3:
total 240
-rwxr-xr-x 1 root root 241540 Apr 26  2015 All.tar.gz

/mnt/To print:
total 22640
-rwxr-xr-x 1 root root  1445717 Mar 13 20:38 Ladies.jpg
-rwxr-xr-x 1 root root 20256122 Mar 13 22:11 Large ladies.pdd
-rwxr-xr-x 1 root root  1445717 Mar 13 20:57 Maleki.jpg
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ 

============================================================

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /mnt/*
-rwxr-xr-x 1 root root 1445717 Oct  5  2012 /mnt/Maleki.pdf
-rwxr-xr-x 1 root root     505 Aug  1  1993 /mnt/PARK.COM
-r-xr-xr-x 1 root root      82 Apr 20  2014 /mnt/READ.ME
-rwxr-xr-x 1 root root   46312 Aug  1  1993 /mnt/SPININFO.EXE
-rwxr-xr-x 1 root root  185165 Aug  1  1993 /mnt/SPININFO.XDB
-r-xr-xr-x 1 root root   94876 Jan  2  1980 /mnt/SPINRIT2.ZIP
-r-xr-xr-x 1 root root  241289 Jan  2  1980 /mnt/SPINRIT3.ZIP
-rwxr-xr-x 1 root root   73810 Aug  1  1993 /mnt/SPINRITE.EXE
-rwxr-xr-x 1 root root  106421 Apr 26  2015 /mnt/Spinrite-II_V20.zip
-r-xr-xr-x 1 root root  101745 Jan 29  1993 /mnt/SPINRITE.ZIP
-rwxr-xr-x 1 root root   90233 Jan 26 21:12 /mnt/TDA7056A.pdf

================================================================
```

The flash drive did not show.  Removed and reinserted.  Shows up with its contents.  Trying to write to it, message "Destination is read only"

Sorry, someday I will re-learn to paste properly in [code] # formatting.  Mental farts happen too often at a certain age...

---

### Post by QDR06VV9 on 2016-04-08
Just Passing through here but this has always worked for me.
You will need a PC running windows, download a program called [SD Formatter]("https://www.sdcard.org/downloads/formatter_4/index.html"), install and reformat the SD card (USB Thumb Drives), making sure the option is set to "ON", it will then be recognized on a Linux machine! without the read only option.
[http://www.digicamhelp.com/accessories/memory-cards/best-way-to-format-a-sd-memory-card/](http://www.digicamhelp.com/accessories/memory-cards/best-way-to-format-a-sd-memory-card/)
[URL="https://www.sdcard.org/downloads/formatter_4/index.html"]https://www.sdcard.org/downloads/formatter_4/index.html

> The SD Association strongly recommends using the SD Formatter instead of formatting utilities provided with operating systems. [/URL]> While formatting tools provided with operating systems can format a  variety of storage media including Secure Digital memory cards, they may  result in lower performance than using the SD Formatter.
 For example, according to the Association, &#8220;SD/SDHC/SDXC memory cards  have a  &#8216;Protected Area&#8217; on the card for the SD standard&#8217;s security  function. Some utilities may format the protected area, SD  Formatter *does not.*
 Using SD Formatter results in better memory cards performance and speed and it improves its overall lifetime.

[URL="https://www.sdcard.org/downloads/formatter_4/index.html"]
[/URL]
Hope this works for you.
Kind Regards

---

### Post by sudodus on 2016-04-08
> **Innernet said:**
> ]Sudodus :  Thanks for your **great** guidance :

-By save files I meant save into the flash drive (write to it).

OK.
> 
At next step (unmount), the system does not recognize my password when requested by the terminal !  It has never been changed !  It has never done that before !  I will pause here until you guide me to fix that.

Edited:  Trying again, got to this:


================================================================

```
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /mnt/*
-rwxr-xr-x 1 root root 1445717 Oct  5  2012 /mnt/Maleki.pdf
-rwxr-xr-x 1 root root     505 Aug  1  1993 /mnt/PARK.COM
-r-xr-xr-x 1 root root      82 Apr 20  2014 /mnt/READ.ME
-rwxr-xr-x 1 root root   46312 Aug  1  1993 /mnt/SPININFO.EXE
-rwxr-xr-x 1 root root  185165 Aug  1  1993 /mnt/SPININFO.XDB
-r-xr-xr-x 1 root root   94876 Jan  2  1980 /mnt/SPINRIT2.ZIP
-r-xr-xr-x 1 root root  241289 Jan  2  1980 /mnt/SPINRIT3.ZIP
-rwxr-xr-x 1 root root   73810 Aug  1  1993 /mnt/SPINRITE.EXE
-rwxr-xr-x 1 root root  106421 Apr 26  2015 /mnt/Spinrite-II_V20.zip
-r-xr-xr-x 1 root root  101745 Jan 29  1993 /mnt/SPINRITE.ZIP
-rwxr-xr-x 1 root root   90233 Jan 26 21:12 /mnt/TDA7056A.pdf

/mnt/Cayman:
total 6400
-rwxr-xr-x 1 root root 2071751 Aug 30  2015 IMG_6820.JPG
-rwxr-xr-x 1 root root 2320995 Aug 30  2015 IMG_6821.JPG
-rwxr-xr-x 1 root root 2143755 Aug 30  2015 IMG_6822.JPG

/mnt/IBM 600E Win98:
total 16
drwxr-xr-x 8 root root 16384 Jul  7  2010 BIOS

/mnt/SpinRite 2:
total 304
-rwxr-xr-x 1 root root    505 Mar  1  1991 PARK.COM
-rwxr-xr-x 1 root root   1763 Mar  1  1991 README.NOW
-rwxr-xr-x 1 root root  36816 Mar  1  1991 SPININFO.EXE
-rwxr-xr-x 1 root root 174201 Mar  1  1991 SPININFO.H!
-rwxr-xr-x 1 root root  47473 Mar  1  1991 SPINRITE.COM

/mnt/Spinrite 3:
total 240
-rwxr-xr-x 1 root root 241540 Apr 26  2015 All.tar.gz

/mnt/To print:sudo
total 22640
-rwxr-xr-x 1 root root  1445717 Mar 13 20:38 Ladies.jpg
-rwxr-xr-x 1 root root 20256122 Mar 13 22:11 Large ladies.pdd
-rwxr-xr-x 1 root root  1445717 Mar 13 20:57 Maleki.jpg
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ 

============================================================

externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ ls -l /mnt/*
-rwxr-xr-x 1 root root 1445717 Oct  5  2012 /mnt/Maleki.pdf
-rwxr-xr-x 1 root root     505 Aug  1  1993 /mnt/PARK.COM
-r-xr-xr-x 1 root root      82 Apr 20  2014 /mnt/READ.ME
-rwxr-xr-x 1 root root   46312 Aug  1  1993 /mnt/SPININFO.EXE
-rwxr-xr-x 1 root root  185165 Aug  1  1993 /mnt/SPININFO.XDB
-r-xr-xr-x 1 root root   94876 Jan  2  1980 /mnt/SPINRIT2.ZIPsudo
-r-xr-xr-x 1 root root  241289 Jan  2  1980 /mnt/SPINRIT3.ZIP
-rwxr-xr-x 1 root root   73810 Aug  1  1993 /mnt/SPINRITE.EXE
-rwxr-xr-x 1 root root  106421 Apr 26  2015 /mnt/Spinrite-II_V20.zip
-r-xr-xr-x 1 root root  101745 Jan 29  1993 /mnt/SPINRITE.ZIP
-rwxr-xr-x 1 root root   90233 Jan 26 21:12 /mnt/TDA7056A.pdf

================================================================
```

The flash drive did not show.  Removed and reinserted.  Shows up with its contents.  Trying to write to it, message "Destination is read only"

Sorry, someday I will re-learn to paste properly in ```
 # formatting.  Mental farts happen too often at a certain age...

I would suggest, that you try the later parts of the test, after **ls -l /mnt/***

Don't worry, that the pendrive does not 'show'. It is obviously visible to the system, since you can list it with the ***ls*** command.

If you wish, you can browse to it with the file browser (***nautilus*** in standard Ubuntu)

[code]nautilus /mnt
```

So I suggest that you unmount and mount it to /mnt according to my previous post. Then try the ***sudo ...*** command line to write to the flash drive, and after that the ***cat ...*** command line, to check that it was really written and possible to read.

```
sudo bash -c 'echo "Hello Superuser World" > /mnt/hello.txt'

cat /mnt/hello.txt
```

I hope this will work, and then the problem is caused by ownership and permissions in your Ubuntu system, which should be fairly easy to fix.

-o-

*Edit:* The tip by *runrickus* looks very interesting, but I am not yet sure that it will solve your problem :-)

---

### Post by Innernet on 2016-04-08
Thanks again. I will proceed per suggestions as soon as my brain restarts working...

Meanwhile, digging here and there, am exposing a portion found on the &#346;ystem log after plugging the flash drive.  May yield clues :

----------------------------------------------------------------------------------

Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.528634] usb 2-3: new high-speed USB device number 3 using ehci-pci
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.661809] usb 2-3: New USB device found, idVendor=1845, idProduct=0104
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.661820] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.661826] usb 2-3: Product: Flash Disk
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.661831] usb 2-3: Manufacturer: USB2.0
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.661836] usb 2-3: SerialNumber: 2009093017073278172
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC mtp-probe: checking bus 2, device 3: "/sys/devices/pci0000:00/0000:00:04.1/usb2/2-3"
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC mtp-probe: bus: 2, device: 3 was not an MTP device
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.789405] usb-storage 2-3:1.0: USB Mass Storage device detected
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.792433] scsi4 : usb-storage 2-3:1.0
Apr  8 16:39:48 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3274.792584] usbcore: registered new interface driver usb-storage
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.795874] scsi 4:0:0:0: Direct-Access     USB2.0   Flash Disk       1.0  PQ: 0 ANSI: 2
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.799284] sd 4:0:0:0: Attached scsi generic sg2 type 0
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.801986] sd 4:0:0:0: [sdb] 1970176 512-byte logical blocks: (1.00 GB/962 MiB)
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.804786] sd 4:0:0:0: [sdb] Write Protect is off
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.804801] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.805715] sd 4:0:0:0: [sdb] No Caching mode page found
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.805720] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.809730] sd 4:0:0:0: [sdb] No Caching mode page found
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.809737] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.810667]  sdb: sdb1
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.816718] sd 4:0:0:0: [sdb] No Caching mode page found
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.816726] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3275.816732] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC dbus[406]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.148922] systemd-hostnamed[2560]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC dbus[406]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.283201] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Apr  8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC udisksd[1918]: Mounted /dev/sdb1 at /media/externet/7C9F-4968 on behalf of uid 1000
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.526776] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.526784] FAT-fs (sdb1): Filesystem has been set read-only
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.548610] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.566070] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.581135] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr  8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.618751] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)

---------------------------------------------------------------------

How do I "run fsck"  suggested above ?

---

### Post by sudodus on 2016-04-08
This is what I suggested in post #2, the last link,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

My first suggestion is to do it in Windows, but if you have no Windows, you can try ***dosfsck*** as described in the link.

---

### Post by Innernet on 2016-04-08
I have some news :
Started the compfuser with the 14.04 live CD.  And as there is not many files to try with, copied the "Example" folder present on the desktop to the 'misbehaving' flash drive by just dragging and dropping with no hurdles. Accepted writing.  Restarted without the Live CD and played that folder; contained two songs .ogg from the flash drive.

With all my ignorance, I do not want to disrespect your expertise. Seems the flash drive is not at fault.  It is something in ownership or permissions or ? that went haywire, and prefer not to risk the flash drive contents by altering its partitions or file systems until something else is tried to force recognition of my 'write rights'.

Does it make sense ?

---

### Post by sudodus on 2016-04-09
You have found out in your own way, that it is possible to write to the drive. Fine :-)

If you change the permissions of the mount point, it will be inherited, when (in the future) you auto-mount a Microsoft file system (typically FAT32) in the USB flash drive. You can and should change the permissions of the mount point, when there is ***no*** USB flash drive, and ***no*** USB hard disk drive connected.

If you do not rely on the current installed system, make a new installed system with the version 14.04 LTS (which works for you live).

I don't know about your computer. If it is very old, use the i386 version (32-bit). It it is middle-aged or newer, you can run the amd64 version (64-bit).

I have tested this with ***ubuntu-14.04.1-desktop-amd64.iso***, made a USB boot drive, installed a test system. In this installed system it works without any problems. When I plug in the flash drive it is auto-mounted and it has read and write permissions (you can create, edit and remove files).

Good luck :-)

---

### Post by mcduck on 2016-04-09
> **Innernet said:**
> I have some news :
Started the compfuser with the 14.04 live CD.  And as there is not many files to try with, copied the "Example" folder present on the desktop to the 'misbehaving' flash drive by just dragging and dropping with no hurdles. Accepted writing.  Restarted without the Live CD and played that folder; contained two songs .ogg from the flash drive.

With all my ignorance, I do not want to disrespect your expertise. Seems the flash drive is not at fault.  It is something in ownership or permissions or ? that went haywire, and prefer not to risk the flash drive contents by altering its partitions or file systems until something else is tried to force recognition of my 'write rights'.

Does it make sense ?
Based on this, yes, there *is* something wrong witht he filesystem on the drive, and it's not just a permission issue. First line suggests that the drive wasn't mounted cleanly and is recognised as possibly corrupted, then there are some actual errors reported on the filesystem, and also one line saying "Filesystem has been set read-only", in other words the OS has mounted it read-only after recognising errors on the filesystem. Fix those, and the drive will mount normally again.
```
Apr 8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.283201] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
Apr 8 16:39:49 externet-Compaq-Presario-CQ60-Notebook-PC udisksd[1918]: Mounted /dev/sdb1 at /media/externet/7C9F-4968 on behalf of uid 1000
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.526776] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.526784] FAT-fs (sdb1): Filesystem has been set read-only
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.548610] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.566070] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.581135] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
Apr 8 16:39:50 externet-Compaq-Presario-CQ60-Notebook-PC kernel: [ 3276.618751] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
```

---

