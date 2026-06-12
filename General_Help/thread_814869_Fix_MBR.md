---
title: "Fix MBR"
date: 2008-06-01
forum: General Help
---

### Post by Accinson on 2008-06-01
Hi,
i have tried to play a bit with dual boot,but something went wrong :)

In the laptop in which i already had Ubuntu and Vista,i installed Mandriva 2008.Since i'm kinda a newbie,i must have done something wrong,because i have never been able to boot it from the Ubuntu grub,which was installed in the MBR.

After some attempts,i did something bad to the MBR,since i am not able to boot anymore.Fortunately,at least,i can boot with the Super Grub cd,but i would like to fix this problem.

By the way,i have already tried the solution based on:
```
grub> root (hd0,4)
grub> setup (hd0)
```
My Ubuntu installation is obviously on my sda5 partition.This didnt work,even though Grub didnt show any error.
Moreover,as i said,i am able to boot with Super Grub CD,but i also tried to fix MBR from it,with no results....

Can you give some advice?

---

### Post by logos34 on 2008-06-01
> **Accinson said:**
> In the laptop in which i already had Ubuntu and Vista,i installed Mandriva 2008.Since i'm kinda a newbie,i must have done something wrong,because i have never been able to boot it from the Ubuntu grub,which was installed in the MBR.

it's not your fault that ubuntu grub won't boot mandriva--I have the same prob. It must be a generalized bug.  I had to write mandriva's grub to a floppy. 

I can boot ubuntu from mandriva's grub on the floppy (and also on the mbr, IIRC). So maybe you could try writing mandriva grub to the mbr, in the off chance that it may clear up whatever the problem is.

I'm thinking that if you added mandriva as a logical partition it may have renumbered the others, which has happened to me repeatedly.

Post the output of

sudo fdisk -l

and 

cat /boot/grub/menu.lst

ADD: by the way, did you specify during mandriva installation that grub be written to the mandriva root partition, or say 'no'?  Because you definitely need mandriva's grub to be installed (I assume it's ubuntu you're booting from SGD)

---

### Post by Accinson on 2008-06-02
Hi logos34,
thanks for your reply :) and sorry for the delay of my answer...

In the meanwhile my situation has changed,since i reinstalled Ubuntu (in the same partition it was before),but before doing that i managed to boot mandriva.
My situation was (but it's similar to the current one):
1)Ubuntu's grub installed on the MBR
2)installed Mandriva's grub but did a mess :) (when it asks for the boot partition i chose the Ubuntu's partition.... :) )
The output of the fdisk -l command was:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4b69985

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       11825    84749308    6  FAT16
/dev/sda3           15095       30401   122953477+   5  Extended
/dev/sda4           11826       15094    26258242+  83  Linux
/dev/sda5   *       15095       18755    29406951   83  Linux
/dev/sda6           30239       30401     1309266   82  Linux swap / Solaris
/dev/sda7           25130       27679    20482843+  83  Linux
/dev/sda8           27680       30238    20555136   83  Linux
/dev/sda9           18756       21942    25599546   83  Linux
/dev/sda10          21943       25129    25599546   83  Linux

Partition table entries are not in disk order
```

I added to the Ubuntu's menu.lst the lines:
```
title Mandriva
root       (hd0,8)
kernel     (hd0,8)/boot/vmlinuz BOOT_IMAGE=Mandriva root=/dev/sda9 resume=/dev/sda6 splash=silent vga=788
initrd     (hd0,8)/boot/initrd.img
```
which is basically what i found on the Mandriva's grub's menu.lst,modifying the root parameter (not using the UUID of the disk).

---

### Post by logos34 on 2008-06-02
So everything is working now? 

Do you still have vista and, if so, is it sda1 or sda2? (may need to fix that partition table --i.e. 'unknown' fs type)

You have two partitions marked boot '*'--might want to fix that.  (in a dual boot only windows should have it).  Use gparted>rightclick on partition>manage flags)

Funny, just before I saw your reply I was fiddling with Mandriva and finally got it to boot from ubuntu grub using the symlink and configfile entries:

> title Mandriva 2008.1 (i586)
configfile (hd0,1)/boot/grub/menu.lst

title Mandriva 2008.1 (i586)
root (hd0,1)
kernel /boot/vmlinuz 
initrd /boot/initrd.img

And when I copied the mandriva entry like you did, it too worked--even using the UUID:

title Mandriva-2008.1
kernel (hd0,1)/boot/vmlinuz BOOT_IMAGE=Mandriva-2008.1 root=UUID=9782591c-f770-4a4a-81ce-0857ee442a51  resume=/dev/hda8 splash=silent vga=788
initrd (hd0,1)/boot/initrd.img

I have wonder why all of a it's working--unless it happened after I used TestDisk recently. (but I would swear the first thing I checked was whether I could boot mandriva from ubuntu grub).

So maybe it's not a bug after all but something else

---

### Post by Accinson on 2008-06-07
Hi and sorry for another delayed answer (i'm having a weird work schedule these weeks :) ),
i'm glad that you succeded in booting mandriva.I plan to play with it a little bit these days,since once i managed to boot it i didn't used it so much (lack of time ...)

As for the partitions,i had noticed those strange things you pointed out:my Vista is in sda2 (i wonder why it says FAT16..);the sda1 should be the restore partition (it uses an "embedded" restore utility) and i dont really know why it says "unknown" type....
I will try to fix these things.

Another thing i don't know the reason of:sda9 and sda10 aren't formatted yet,but fdisk says that they're "linux" type.I wonder why....

Thank you for the advices :)

---

### Post by logos34 on 2008-06-07
In dual boot setups the partition table occasionally gets messed up to the point where the fs type shows up wrong in fdisk or Gparted sees the entire disk as 'unallocated' (something that happened to me recently), among other things.  The presence of logical partitions only seems to increase the likelyhood of this.  Your data (on vista) is probably fine, but you might want to consider fixing the (DOS) partition table with TestDisk.  I've used it a number of times successfully.  Just make sure you read the docs first and don't write any changes to the disk until you're absolutely certain.

I might play with mandriva today.  It seems to me about the best distro out there in terms of migrating windows users to linux.  I've installed some XP-like themes and icons, plus IE 7 theme for firefox.  (I'm trying to convert a senior citizen who uses XP Home).  

For some reason the KDE desktop seems lighter than gnome on my ubuntu. I had always thought it used MORE ram, not less.  

KDE4 looks promising, but in actual use seems half-baked.  They've changed a number of global keyboard shortcuts too, which is a little frustrating.

---

