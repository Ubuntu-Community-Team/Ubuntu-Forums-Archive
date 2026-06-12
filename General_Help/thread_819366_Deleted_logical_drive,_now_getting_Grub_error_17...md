---
title: "Deleted logical drive, now getting Grub error 17..."
date: 2008-06-05
forum: General Help
---

### Post by s8v4o on 2008-06-05
Hi all, a linux newb here needing a little help.  On one of my computers I'm running a dual boot setup with XP and Ubuntu 7.10.  Everything was fine till I started running out of disc space in ubuntu.  I tried using Gparted to resize my windows data partition and even though I had that partition unmounted the option to resize was greyed out.  This isn't a problem on my other box running Ubuntu 8.04 as it seems to have much better NTFS support right out the box.  
I HAD the drive setup as three partitions initially. A windows patrition (hdb1), ubuntu root (hdb2), ubuntu swap (hdb3), and the data partition (hdb4), and the boot loader was installed on hdb0.  So I booted into windows to deleted the data partition so I could then go into linux and resize my small ubuntu partition.  I should have left it alone after deleting the partition but my dumb **** deleted the logical drive as well thus getting rid of the swap partition that windows saw as free space I'm assuming.  At first I thought I lost everything in linux but after looking this morning using the live CD I still have my root partition and my XP partition.  It appears that all I lost was the swap partition.  If all I lost was the swap partition why is grub having problems?  Is it because grub is actually okay and my only issue is the missing swap partition or am I totally wrong here?
I going off of memory here as I'm currently at work.  I actually browsed my root partition using the live disc and all seems to be fine there.  So my question is what should I do to repair my linux install?  I realize that I'll have to redo the swap partition but is there anything else?  Did I screw up grub somehow?  I tried booting with the live disc and running "fixmbr" but it said it couldn't find the kernel.  Thanks for reading all this crap.

---

### Post by rraj.be on 2008-06-05
Just try reinstalling GRUB.

Because

GRUB error 17 is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

To reinstall gru boot into live cd.

open in terminal as 

```
sudo grub

find /boot/grub/stage1
```

if it returned like hd(x,y)

then type 

```
root (x,y)
setup (x)

quit

sudo reboot
```.


now it should work for you.

---

### Post by Zorael on 2008-06-05
Well, provided you can recreate a swap partition, the only things you need to do is reinstall grub into the MBR and make sure your /etc/fstab is sound. This will need to be done from a live CD environment (or equavilent), of course.

```
$ sudo grub

grub> find /boot/grub/stage1
 (hd**x**,**y**)		*<note what **x** and **y** are, may be (hd0,1), may be (hd4,8), etc>*

grub> root (hd**x**,**y**)

grub> setup (hd**x**)	*<note, no **y**>*

grub> quit

$ sudo update-grub	*<for good measure>*
```

As for your fstab, open it up and compare the first column (filesystems/device nodes) with the output from 'sudo fdisk -l'. You should be able to figure out which partition is which from their sizes. Do note that if the fstab does not refer to their device nodes and instead their UUIS, these *will* likely need to be updated. There is a command to divine these UUIDs, but entering their /dev/sd* nodes does the trick as well.
```
$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7f1f7f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3404    27342598+  83  Linux
/dev/sda2            3405        4864    11719839    f  W95 Ext'd (LBA)
/dev/sda5            3405        3647     1951866   82  Linux swap / Solaris
/dev/sda6            3648        4864     9767972   83  Linux

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc		/proc		proc	defaults 0 0
/dev/sda6	/		ext3	relatime,errors=remount-ro 0 1
/dev/sda1	/main		ext3	relatime 0 2
/dev/sda5	none		swap	sw 0 0
/dev/scd0	/media/cdrom	udf,iso9660 user,noauto,exec,utf8 0 0

```

---

### Post by s8v4o on 2008-06-05
Thanks for the response guys!  I'll try these fixes as soon as I get home.  When you say using a live CD, I'm assuming that I don't let it fully load right?  Just F5 (or F6 cannot remember) it and get a command line then go from there?   
I can recreate a swap file that shouldn't be a problem.  My question is if the swap file isn't exactly the same will ubuntu have issues since it will more than likely start and end at different sectors?  Thanks again for the help guys.

---

### Post by rraj.be on 2008-06-05
NOT AT ALL.

Live cd means you should boot completly into live cd.

Then open terminal from Applications --> Accesories --> terminal.

First fix your grub>

Then you can deal easily with your swap.

There is no use of swap without any working OS

---

### Post by s8v4o on 2008-06-05
Okay guys I fixed the grub but am having difficulty with the swap file.  To be more specific I've created the swap file, did the fdisk -l to see what's where, but I can't seem to be able to edit my fstab on my root partition.  When I try to gedit my fstab the fstab on the live cd comes up.  When I browse the actual partition and manually open my original fstab I can open it, but do to restrictions I'm unable to save it.

I've also tried to 

sudo gedit /hdb2/etc/fstab 

but this tells me that file doesn't exist.  How do I open my original fstab so I can make the proper changes?

EDIT  Nevermind, I was telling gedit the wrong place.  Now I'll see if the changes work.

---

### Post by rraj.be on 2008-06-05
To add swap try this.

[This will guide to add Swap file and not to add a swap partition]

1--> CREATE A SWAP FILE.
-----------------------
```

sudo dd if=/dev/zero of=/mnt/1024Mb.swap bs=1M count=1024
```

This will create a 1GiB swap file on /mnt

This 1024 can be a value that you want your swap size should be.

[1024 is optimal and more than enough]

2--> Formatting that file to create a swapping device :
-------------------------------------------------------

```
sudo mkswap /mnt/1024Mb.swap
```



3-->Adding the swap to the running system :
-------------------------------------------
```

sudo swapon /mnt/1024Mb.swap
```


4)--> Making the change permanent :
-----------------------------------
      edit your /etc/fstab:

```

      sudo gedit /etc/fstab
```



      and add this line at the end of the file:

      ```
/mnt/1024Mb.swap  none  swap  sw  0 0
```


     
5)--> save and reboot

Now you will be having a 1024 MiB of swap in /mnt.


Hope this helps you.

may i know if you have problem still.

---

### Post by s8v4o on 2008-06-06
Thanks, I'll try that when I get home.  So are there multiple ways to create the swap then?  I always thought the swap had it's own partition unless using something like LVM?  The way you are suggesting just creates the swap inside the root partition then?  If so are they are performance differences doing it that way?

Here's where I left off last night.  I tried booting with the current configuration as seen in the screenshot provided.  When I try to boot it says the following :

ERROR 17: cannot mount selected partition

Here's the screenshot of my settings (fdisk -l, fstab, and Gparted open)
[http://i195.photobucket.com/albums/z7/s8v4o/Screenshot.png]("http://i195.photobucket.com/albums/z7/s8v4o/Screenshot.png")

As I said though, I'll try that suggestion when I get home. I appreciate the help.

---

