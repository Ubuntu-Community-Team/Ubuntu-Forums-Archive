---
title: "fsck freezes every time"
date: 2007-04-25
forum: General Help
---

### Post by Chang An on 2007-04-25
Hi all,
After several failed attempts to install Feisty I finally got it installed.  I got the restricted drivers working for my nvidia card and I could boot and log out of the GUI flawlessly.  Now a new problem popped up.  Every time I try to boot a disc check is forced and it just hangs and never finishes.  I cant get into recovery mode ether or use the live cd because the live cd cant boot into the GUI do to the nvidia driver issue.  Any help would be great.

---

### Post by Chang An on 2007-04-25
Also Im running a dual boot system with w!$#@s XP

---

### Post by Chang An on 2007-05-20
any help?

---

### Post by Herman on 2007-05-20
Hello Chang An,
You should download a [GParted -- LiveCD]("http://gparted.sourceforge.net/") .iso and burn that to disk. Boot the [GParted -- LiveCD]("http://gparted.sourceforge.net/") and when it is running just right-click the partition you want to check and click 'check'. Then click 'Apply' on the toolbar, and a confirmation box will appear. Click the 'Apply' button.
You will see a new window with a reciprocating bar and a progress bar, and under that, a small triangular button marked 'Details'. You can click that or wait until the check is finished, it will show you what happened. GParted runs e2fsck -f -y -v /dev/hdx for you if you have an ext3 file system. That should fix it, I hope. Good luck, Regards, Herman :D

---

### Post by Chang An on 2007-05-21
Thanks for the advice
The GParted Live cd freezes every time I try to use it though.  I think the force check should not be used in recovery mode.  Mostly because thats the thing Im trying to recover from. :p
I feel the devs should have offered a way to still access the command line if the fsck freezes every time.  The keyboard shortcuts to skip the Fsck don't work as well.  Any other ideas?

---

### Post by mcduck on 2007-05-21
Start the machine with any live-cd, mount the disk and check your /etc/fstab. If any of your windows drives has '1' as the last number in their entry lines change them into '0'. This will disable fsck fo those drives, which might solve your problem..

---

### Post by Chang An on 2007-05-22
I can't run the live-cd because it fails to use the right video driver.  It boots and I just get a black screen.  Thats why I had to install feisty with the alternate install cd.  Do you have any other ideas?  Thanks

---

### Post by mcduck on 2007-05-22
Are you using Ati's X-series video card? Try 6.06 or 6.10 desktop-cd's, they should work fine. It's just the 7.04 that doesn't work for those cards..

Or try if you can boot into recovery mode (from Grub menu)

---

### Post by mozetti on 2007-05-22
As has been mentioned, your best bet is to boot some sort of Live CD (Ubuntu, Knoppix, etc -- whatever works) and then do a fsck check on whichever partition is hanging during the normal boot processs. Or, just do an fsck check on all of the non-NTFS partitions to make sure they are all clean.

---

### Post by Chang An on 2007-05-23
Hi,
I finally booted into an Edgy live cd.  Im having trouble mounting my system partition to work on it though.  I can't add the disk mounter icon to the panel and using sudo mount /dev/sda2 does not work.  Any ideas how I can mount my system partition from the live cd?

---

### Post by Herman on 2007-05-23
Hello Chang An,
We should never run a file system check on a partition while it is mounted. It is best to leave it unmounted and run your file system check.
```
e2fsck -f -y -v /dev/sda2
```When the file system check is finished then you can mount it.

To mount a partition, first you need to make a directory somewhere to mount it in. This directory is also called a 'mount point'. You mount point can be anywhere, but the normal places to make a mount point are either in the /mnt directory or the /media directory. In Ubuntu we use the /media directory most of the time.  A command like this one will make a mount point,
```
sudo mkdir /media/ubuntu
```
Next, we mount our partition with a command like this,
```
sudo mount -t ext3 /dev/sda2 /media/ubuntu
```Now it should be mounted.

Regards, Herman

---

### Post by mozetti on 2007-05-23
Nice job on the instructions, Herman.

I just wanted to say that every time I come across your posts, they are all very informative and helpful. Great  job!

---

### Post by Chang An on 2007-05-23
Thank you very much Herman!
Those commands did the trick.  Once I could access my system partition I edited my /etc/fstab file and now I can boot into Ubuntu. :p 
I will have to run fsck manually from now on.

---

### Post by Herman on 2007-05-24
Thanks  mozetti, 
Yes, I think it's worth some extra time and typing to try to make sure everything is well explained. I still remember when I was new here and I found it very difficult to get started because it seemed as if you had to know Linux already to understand the answers most people were being given. The answers were a little too breif.  If a person already knew Linux then they wouldn't need to ask. So I like to give verbose answers. Thank you for your encouragement, it's nice to know the extra effort is appreciated. :D

You are welcome Chang An,
So it was a problem in your /etc/fstab? I'm glad you have it fixed now, well done. :D

For a normal file system check (when there is nothing actually wrong), I just run a preening type of file system check instead of a repairing one. This is the command I like to use most of the time for my regular file system checks,
```
sudo e2fsck -C0 -p -f -v /dev/sda2
``` I run that from a live CD and if it's just for tidying things up in my file system and fixing everything it can fix automatically.
Then if that file system check finds something it can't fix automatically, it will let me know by giving me a message something like this,
>                               /dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options). 
 If I get a message like that, it is then that I run ```
sudo e2fsck -f -y -v /dev/sda2
``` That does a repair type of file system check.

Regards, Herman :D

---

