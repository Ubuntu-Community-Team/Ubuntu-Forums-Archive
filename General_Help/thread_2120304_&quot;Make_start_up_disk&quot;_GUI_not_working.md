---
title: "&quot;Make start up disk&quot; GUI not working"
date: 2013-02-26
forum: General Help
---

### Post by ACon125 on 2013-02-26
Hi everybody, can everyone give me an advice about "Make start up disk" GUI?  I love to use this tool to create live USB because is straight forward and beginner friendly , however it does not seems to work in my system. I can't load any .iso file in the upper dialog box.
To be more accurate I can select my .iso file using "other" button however the selection is always ignored and I cannot proceed with disk creation.  Am I missing something or there is a problem with  it? I'm using Xubuntu 12.04.
Thanks for your help

---

### Post by sudodus on 2013-02-26
Will this method work for you?

```
usb-creator-gtk -i candidate.iso
```Use the real /path/name to the iso file you want to use. See ```
man usb-creator-gtk
``` for more details.

---

### Post by ACon125 on 2013-02-26
> **sudodus said:**
> Will this method work for you?

```
usb-creator-gtk -i candidate.iso
```Use the real /path/name to the iso file you want to use. See ```
man usb-creator-gtk
``` for more details.
Hi, thanks for your kind suggestion.
I had a go using -i option as you suggested;
I had this output 
isoinfo: Unable to find Joliet SVD
program was actually launced but  file wasn't loaded and still make start up disk button was disabled.
Moreover I installed imageWriter and even that failed to upload my .iso file (I navigated to the folder containing .iso files but the program did not detect any of them)

---

### Post by sudodus on 2013-02-26
> **ACon125 said:**
> Hi, thanks for your kind suggestion.
I had a go using -i option as you suggested;
I had this output 
isoinfo: Unable to find Joliet SVD
program was actually launced but  file wasn't loaded and still make start up disk button was disabled.
Moreover I installed imageWriter and even that failed to upload my .iso file (I navigated to the folder containing .iso files but the program did not detect any of them)
I think it is another problem, not with usb-creator-gtk or imagewrite. Maybe your computer cannot read the iso files.

Can you try with a terminal window to list the file and its permissions?

Change directory with cd to the directory where you have the an iso file. You can drag and drop the directory from the file browser Thunar (the blobs at the top of the thunar window)

```
cd /path-to-iso-file/
```
```
ls -l candidate.iso
```
and post the output of the command in a reply

***Edit***: Joliet indicates a CD or DVD. Is your iso file on a CD or DVD? Or are you ***opening*** the file instead of just selecting it to be imaged to the USB drive?

---

### Post by ACon125 on 2013-02-26
output is like this
```
-rw-rw-r-- 1
```and yes there is no CD or DVD involved, I downloaded the file and saved on the HDD
(...yes I'm a newbie if someone is still wondering  :-\")
thanks for your help

---

### Post by sudodus on 2013-02-26
> **ACon125 said:**
> output is like this
```
-rw-rw-r-- 1
```and yes there is no CD or DVD involved, I downloaded the file and saved on the HDD
(...yes I'm a newbie if someone is still wondering  :-\")
thanks for your help
Read and write for user and group, read only for others. So the file should be readable for everybody.

1. But please show the whole line (change your user name to user, if you don't want to show it).

2. And what about your USB drive, which you want to make bootable with Ubuntu? Please insert it, mount it (if possible) using the file browser and post the output of the following commands

```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```

These commands will show drives, partitions and file-systems available and mounted (internal as well as external drives). I hope to understand if your USB drive is properly partitioned and formatted from this information.

---

### Post by ACon125 on 2013-02-26
I followed your instruction, these are the output I obtained

> **sudodus said:**
> 

1. But please show the whole line (change your user name to user, if you don't want to show it).

```
-rw-r--r-- 1 user user 725921732 Feb 25 23:47 lubuntu-12.10-desktop-i386.iso
```> **sudodus said:**
> 
2. And what about your USB drive, which you want to make bootable with Ubuntu? Please insert it, mount it (if possible) using the file browser and post the output of the following commands

```
sudo fdisk -lu
``````
sudo blkid
``````
df
```These commands will show drives, partitions and file-systems available and mounted (internal as well as external drives). I hope to understand if your USB drive is properly partitioned and formatted from this information.
```
sudo fdisk -lu
``````

Disk /dev/sdc: 2003 MB, 2003828736 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
``````
sudo blkid
``````
/dev/sdc: SEC_TYPE="msdos" LABEL="USB DISK" UUID="0012-D687" TYPE="vfat" 
```and finally

```
df
``````
/dev/sdc         1956608      672   1955936   1% /media/USB DISK
```For the sake of brevity I omitted info about hard disk partitions but I can post it if required.

---

### Post by sudodus on 2013-02-26
It's fine with the info you provided :-)

The iso file is yours (not any strange ownership). And the size is reasonable for Lubuntu (I did not check it, but it should be what it is supposed to be).
--
But there is one strange thing with the USB drive. The file system sits on the whole drive. There is no separate partition from the identity of the drive itself. When we edit partitions with ***gparted*** on a HDD, SSD or USB flash drive (pendrive), there is the drive name **[FONT="Courier New"]/dev/sdx[/FONT]** with the drive letter x, in your case c for the third drive. Then the partitions on the drive have numbers y so the block device name will be **[FONT="Courier New"]/dev/sdxy[/FONT]**, in your case it should be 1 if only one partition. **But there is no partition [FONT="Courier New"]/dev/sdc1[/FONT]**

It could be mounted according to the output of ***df***, and maybe you can read and write files on that pendrive. But I think it will make the USB creator programs confused.

I suggest that you try to change it. Install gparted into your working Xubuntu with
```
sudo apt-get install gparted
```
Then run it with
```
gksudo gparted
```
- Select the pendrive at the top right corner of the gparted window. Make sure it is the pendrive (check the size of it).

- Select Device -- Create partition table
and make an MSDOS partition table (the standard one with MBR etc)

- Select Partition or right-click on the graphic field representing the drive space and create a new partition

- Format the partition to FAT32.

- Add a suitable label, for example USB-LU

- Finally [COLOR="SeaGreen"]click on the tick icon[/COLOR] at the top of the gparted window to perform the operations on the USB drive.

And you should be ready to run ***usb-creator-gtk*** again, but maybe you'll want to check that there is really a partition **[FONT="Courier New"]/dev/sdc1[/FONT]** first.

---

### Post by ACon125 on 2013-02-27
hi there,
first of all thanks so much for your help. I truly appreciate your support 
nevertheless I'm still stuck.  I installed gparted and run it following your suggestion but something went wrong and I had the following error message (see pic) moreover the USB drive failed to  mount since then.
I'm kind of ready to give up.

---

### Post by sudodus on 2013-02-27
No don't give up yet. It is time to get the supertool ***dd***, nick-named 'disk destroyer'. dd is tool, that can write on devices, partitions and file systems at a very low level if necessary. It does what you tell it to do, and asks no questions. So if you ask it to do something stupid, for example wipe your internal drive, that is not backed up, it will wipe it.

But if you know what to do and tell it to do that, it does miracles. But back to engineering language again ...

As long as you have not changed the naming of your devices, so that the USB pendrive remains at **/dev/sdc**, change directory to where you have the lubuntu iso file. And then run this command

```
sudo dd if=lubuntu-12.10-desktop-i386.iso of=/dev/sdc bs=4096
```

It asks no questions and won't tell you anything either until it has finished, unless you kick on it with a kill command from another terminal window.
```
ps -A|grep " dd$" 
```

and use the [COLOR="SeaGreen"]four digit number from the output[/COLOR] in the next command, for example
```
sudo kill -USR1 [COLOR="SeaGreen"]5441[/COLOR]

```That should produce a few lines showing how much it has written and at what speed.

When dd has finished you have a boot drive. The USB drive has the same file system on it as if it were a CD disk.

Good luck :-)

---

### Post by ACon125 on 2013-02-28
Hi sudodus,
I can't thank you enough. dd did actually the job exactly as you described, no question asked and problem solved.
Considering my awkwardness using CLI I did hold the breath while it was working, luckily it didn't take long. 
I really learnt a lot along the way. Thanks again!
Now I'm off to play with my new lubuntu !

---

### Post by sudodus on 2013-02-28
You are welcome :-)

---

### Post by roel_guldemond on 2013-10-14
Seems that I was having same problem.
I downloaded Xubuntu 12.04
Using Startup Disk Creator, I couldn't load the Xbuntu-.iso file in the first field (Source disk image .iso or CD).

However that is what **thought**

In fact I could choose in this field for the xbuntu-iso.
But I did not see this xbuntu-iso,
as the field seemed to only show the ubuntu.iso.
But when I hovered at the end of the field, suddenly there appeared a small scroll bar.
And scrolling down, resulted in seeing the Xbuntu-.iso file!!
Which could be selected :)

---

