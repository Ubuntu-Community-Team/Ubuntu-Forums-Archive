---
title: "Deleting sda5, when my main mount point is sda7 ?"
date: 2007-07-05
forum: General Help
---

### Post by Raziekiel on 2007-07-05
I installed Ubuntu in a dual boot setup originally, and I've gotten rid of windows now, and I just want to make my whole drive linux, however, I can't delete my old windows partition!

I have 10g unpartitioned at the front of the drive, then and Extended partition that has sda5 (Old windows, 122gigs) sda6 (2gig swap) and sda7(my main mount point).

When I try to delete sda5 Gparted tells me I have to unmount all devices above it first, but how do I unmount my swap and main partition??
I'm totally lost on what to do here:confused:

Here's a picture just in case I didn't explain that all too well. [http://www.imagedump.com/index.cgi?pick=get&tp=507387]("http://www.imagedump.com/index.cgi?pick=get&tp=507387")

---

### Post by Happy_Man on 2007-07-05
You will have to boot a LiveCD, and delete the partitions from there by going to System --> Adminstration --> GNOME Partition Editor from the LiveCD. The reason for this is that for a logical partition to be deleted, the extended partition above must be unmounted, but unfortunately, you can't do that from your install, since it also relies on a partition stored under the extended. So, to delete that partition, you would have to tell the computer to disregard the partition with information it's using to run itself.

---

### Post by Raziekiel on 2007-07-05
Alright I booted from CD and deleted the partition, however my mount point is still stuck at the end, and I can't merge it with the unallocated space =(

Is it possible to make a partition at the front of my drive, in the open space, and copy all of / onto the new partition?

Heres a screen of what it looks like now: [http://www.imagedump.com/index.cgi?pick=get&tp=507394]("http://www.imagedump.com/index.cgi?pick=get&tp=507394")

Thanks for the help by the way =D

---

### Post by Raziekiel on 2007-07-06
Ok, I resized my main partition ( /) and copied it to the front of the drive where windows used to be using the Gnome Partition Editor.
Now, I know I need to change GRUB since I want it to boot from a different partition, sda1 instead of sda7, however when running on live cd, it won't mount either of the partitions, sda1 or 7, so I don't know how to get to the grub config file:(

---

### Post by mbeierl on 2007-07-06
According to the image, sda7 is now known as sda5...  Try that?

---

### Post by logos34 on 2007-07-06
to mount partition from live cd:

sudo fdisk -l 

should show / partition as /dev/sda1

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo gedit /mnt/ubuntu/boot/grub/menu.lst

change 'groot' + 'root' lines from (hd0,6) to (hd0,0).  I believe you can leave the UUID's alone on the kernel lines (but if it's using '/dev/sda7' instead of UUID then you'll have to change it to sda1).

Check fstab so the partition mounts:

sudo gedit /etc/fstab

If using UUID format, it should work.  Otherwise you'll need to change to /dev/sda1  / ext3 ...

---

### Post by logos34 on 2007-07-06
> **mbeierl said:**
> According to the image, sda7 is now known as sda5...  Try that?

Ok, so I see you've just posted a new shot in which its become sda5...I thought you said you resized / copied it to the unallocated space at the beginning of the disk.

---

### Post by Raziekiel on 2007-07-06
> **logos34 said:**
> Ok, so I see you've just posted a new shot in which its become sda5...I thought you said you resized / copied it to the unallocated space at the beginning of the disk.

I did, sorry let me get a new screenshot up, I"ve been messing with it a bit.
I tried your suggestions, editing the grub files, and I get GRUB Error 22 when I try to boot, so it's still not finding something.
[http://www.imagedump.com/index.cgi?pick=get&tp=507523]("http://www.imagedump.com/index.cgi?pick=get&tp=507523")
Ok, so sda1 is the copy of my old partition. sda3 is the new swap, sda5 is the old partition.

Here is my fstab:
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

```

and my grub:
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0groot)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=f5d0ee16-ba79-4e87-8dc8-37f2c870a2a2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault
```

---

### Post by logos34 on 2007-07-06
'groot' line is near the top:

> ## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,[COLOR="Red"]0[/COLOR])**

------------------

Not:

> root		(hd0,0groot)

But this:
> root		(hd0,0)

Add a line to fstab for root:

> **/dev/sda1 / ext3 defaults 0 1** 

or

> **/dev/sda1 / ext3 defaults,errors=remount-ro 0 1**

After you edit menu.lst, rewrite grub to the mbr:

> [B]sudo grub
find /boot/grub/stage1[/B]
(it should return '(hd0,0)'--enter in next command)
[B]root (hd0,0)
setup (hd0)
quit[/B]

---

