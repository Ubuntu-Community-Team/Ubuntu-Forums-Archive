---
title: "Swap Partitions and Drive Mounts"
date: 2008-05-06
forum: General Help
---

### Post by Cyber Akuma on 2008-05-06
I have the latest version of Ubuntu, there are two things I want to know how to do:

1:
I have 1.5 gigs of unpartitioned space left on my drive, and it would be a real mess with the way my HDD is right now to resize the linux partition, so I decided to just create a swap partition.

When I tried to google this however, I actually wasnt able to find a guide, most just lined to web forums or wanted me to create a swap file instead.

Can anyone tell me how to create and setup a swap partition?

2:
I have multiple operating systems with multiple file systems in different partitons on my drive. Ubuntu has no trouble reading all of these, but I have to manually mount them every time.

Is there any way I can set it so they are mounted and appear as an icon/shortcut on my desktop on boot?

Thanks

---

### Post by smoker on 2008-05-06
install 'gparted' from the synaptic package manager, open this, and highlight the unpartitioned space, create, and choose 'swap' partition, and apply.

as to mounting partitions automatically, you will have to edit the 'fstab' easier to give you this link than me to try to explain it badly!
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

best of luck

---

### Post by Cyber Akuma on 2008-05-06
But how do I configure Ubuntu to use the swap partition after I create it?

---

### Post by bodhi.zazen on 2008-05-06
> **Cyber Akuma said:**
> But how do I configure Ubuntu to use the swap partition after I create it?

You will need to manually update fstab :

```
/dev/sdxy swap swap defaults 0 0
```

You can also 

```
sudo swapon /dev/sdxy
```

Where /dev/sdxy == your swap partition.

---

### Post by Cyber Akuma on 2008-05-06
[QUOTE=bodhi.zazen;4897696]You will need to manually update fstab :

```
/dev/sdxy swap swap defaults 0 0
```

How would it know where my swap partition is with that command?

Also, where is this fstab file?

I used to have a swap partition, but I needed to delete it, now im trying to re-create it.

I remember I needed to comment it out of this one text file, but it contained a UUID, wouldent I need to get the new UUID of the swap partition I created?

Back when I tried moving Ubuntu to a new partition I coudlent get it to boot until I used the live cd to get my new UUID and edit my menu.lst file with the new ID.

---

### Post by bodhi.zazen on 2008-05-06
First make a swap partition. You can do this with gparted on the live CD if you like. Take note of the partition (/dev/sd**).

Then boot back to ubuntu on your hard drive.

You should already know the swap partition. If you need, list your partitions with :

```
sudo fdisk -l
```

You can use /dev/sd** in fstab, or UUID.

To list your partitions by UUID :

```
sudo blkid
```

Now edit fstab 

```
gksu gedit /etc/fstab
```

Add a line for your new swap, 

either

```
/dev/sd** swap swap defaults 0 0
```

or 

```
UUID=xxx.yyy.zzz swap swap defaults 0 0
```

where /dev/sd** == your swap partition (from fdisk) or UUID=xxx.yyy.zzz = your swap partition (from blkid).

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Cyber Akuma on 2008-05-07
Ok, that should setup my swap partition, thanks. :)

How can I check that it's working?

Also, how would I go about creating the shortcuts to my other partitions?

I want them to appear as icons on my desktop, my home folder and the different partitions I have on my system. I can temporarely mount them, but after rebooting they disappear.

---

### Post by VMC on 2008-05-07
SWAP is in my fstab , but it is not swapon. I have to use gparted each reboot. How do I make that permanent?

fdisk -l output ====
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3200    25703968+  83  Linux
/dev/sda2            3201        3576     3020220    5  Extended
/dev/sda5            3201        3576     3020188+  82  Linux swap / Solaris

$ sudo blkid output ===
/dev/sda1: UUID="d8533154-cef1-4cce-a823-9f3f74aab65b" TYPE="ext3" 
/dev/sda5: TYPE="swap"

fstab output ===
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d8533154-cef1-4cce-a823-9f3f74aab65b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0703bda2-3d0b-42e5-9d49-5c2634a4bd53 none            [COLOR="Red"]swap[/COLOR]    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by bodhi.zazen on 2008-05-07
> **Cyber Akuma said:**
> Ok, that should setup my swap partition, thanks. :)

How can I check that it's working?

Open a terminal and type 

```
free
```

> Also, how would I go about creating the shortcuts to my other partitions?

I want them to appear as icons on my desktop, my home folder and the different partitions I have on my system. I can temporarely mount them, but after rebooting they disappear.

If you want them as icons on your desktop mount them in /media.

To have them appear in other locations use link

ln -s /media/drive1 ~/drive1

change "drive1" to the name of your mount point in media.

---

