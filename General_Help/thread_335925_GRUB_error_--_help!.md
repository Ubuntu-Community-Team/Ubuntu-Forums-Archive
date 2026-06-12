---
title: "GRUB error -- help!"
date: 2007-01-10
forum: General Help
---

### Post by alyson on 2007-01-10
Earlier today, I used Acronis to delete my Dell Restore partition and add the new space to my Ubuntu partition.  I also added some extra space from my Windows partition to my Ubuntu partition.  Once the process was finished, I was greeted with error 15 on GRUB, and was unable to boot into anything.  I followed a forum post related to a similar issue, and entered 

```
sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0)
quit
```

into a terminal in the LiveCD.  This allowed GRUB to load properly.  Ubuntu and Windows both showed up, and I now can boot into Windows without a problem.  Unfortunately, I still can't boot into Ubuntu; when I try, I receive error 15: file not found. 

I assume I just need to point GRUB to the correct place, as some partitions were moved around (thought I may well be wrong), but I don't know how to do this, or even if this is what I need to do.  Also, I can access the files in my Ubuntu partition via Explore2fs in Windows, so I think everything is intact (?).  I found a few posts that said something about editing /boot/grub/menu.lst, but I don't know how to access this file via the live CD.  Do I need to mount my Ubuntu partition?  And if so, how do I do this?  

Anyway, here's my fdisk -l output (I don't know why Acronis gave me a bunch of extra small partitions--I certainly didn't try to configure it as such):

```
Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3093    24804360    7  HPFS/NTFS
/dev/sda4            3094        9546    51833722+   5  Extended
/dev/sda5            3094        3219     1012063+  83  Linux
/dev/sda6            3220        9487    50347676   83  Linux
/dev/sda7            9488        9488        8001   83  Linux
/dev/sda8            9489        9546      465853+  82  Linux swap / Solaris
```

Anyway, I hope someone can help me!  I'm hoping I won't have to reinstall.  Oh, and I also tried to use the Super GRUB disk, but that didn't seem to help, unless I overlooked an option.  Thanks!

---

### Post by po0f on 2007-01-11
alyson,

Which of those partitions contains the /boot directory?

---

### Post by alyson on 2007-01-11
How do I find out?  (I'm sorry...)

---

### Post by alyson on 2007-01-11
I'm assuming it's in sda6, which is my main Ubuntu partition, or in sda1, which is (I think) my MBR.

---

### Post by po0f on 2007-01-11
alyson,

No worries, just boot the live CD.  When it gets all started up, open up a terminal (Applications->Accessories->Terminal).  For all your Linux partitions (/dev/sda5, /dev/sda6, /dev/sda7), make corresponding /mnt directories.  Then just list the contents of those directories, it should be obvious after doing so:
```
[FONT="Courier New"]$ mkdir /mnt/sda5 /mnt/sda6 /mnt/sda7
$ mount /dev/sda5 /mnt/sda5
$ mount /dev/sda6 /mnt/sda6
$ mount /dev/sda7 /mnt/sda7[/FONT]
```

Then just run `ls` in those directories.  Whichever one contains /boot, well, contains the /boot directory.  From here, you should be able to edit menu.lst.

Assuming it was in /dev/sda6:
```
[FONT="Courier New"]$ gedit /mnt/sda6/boot/grub/menu.lst[/FONT]
```

[EDIT]

[quote=alyson]I'm assuming it's in sda6, which is my main Ubuntu partition, or in sda1, which is (I think) my MBR.[/quote]

I think it's in /dev/sda6 as well.

---

### Post by alyson on 2007-01-11
Awesome!  It was sda6.  Okay, so just to make sure I'm doing this correctly, I want to change all of the "root" options to (hd0,5) in this, right?:

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot
```

---

### Post by po0f on 2007-01-11
alyson,

Yes.  I figured when you said that you deleted the OEM partition to create a new Linux partition that it bumped all your drive numbers off by one.  (They tend to put those towards the beginning of the drive.)

[EDIT]

Did you change /etc/fstab any to accommodate these changes?

---

### Post by alyson on 2007-01-11
Hm.  It's almost there, I think, as Ubuntu started to boot up, but then I received this message:

bin/sh: can't access tty; job control turned off
(initramfs)

Does this have something to do with not changing /etc/fstab?

EDIT:
Oh, and also, in my menu.lst should I change these:
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
to these:
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda**6** ro quiet splash
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda**6** ro single

---

### Post by po0f on 2007-01-11
alyson,

It might.  You have all your Ubuntu partitions identified by UUID in /etc/fstab, correct?  Just change them to the actual device.  So instead of "UUID=<a_bunch_of_crap>", use "/dev/sdaX".  If this was a default Edgy install, there should be comments showing what partitions correspond to which device entry.  Just remember to add one to the /dev/sda**5** entry, it's 6 now (or should be).

Post your /etc/fstab if you have any doubts.

---

### Post by alyson on 2007-01-11
I'm worried about messing up something (as if I haven't already), so here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=9c31bcf4-92fe-491f-913e-036825b07881 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D6-011C  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=D888071D8806F9B0 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda3       /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=0bd47f9c-cf6a-47e9-bd24-cdaf7cab38f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

And should I change these to show sda6 in my menu.lst?
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single

---

### Post by po0f on 2007-01-11
alyson,

You can make the following changes from:
```
[FONT="Courier New"]# /dev/sda5
UUID=9c31bcf4-92fe-491f-913e-036825b07881 / ext3 defaults,errors=remount-ro 0 1[/FONT]
```
to:
```
[FONT="Courier New"]# /dev/sda6
/dev/sda6 / ext3 defaults,errors=remount-ro 0 1[/FONT]
```

[EDIT]

Change the swap partition's device as well:
```
[FONT="Courier New"]# /dev/sda6
UUID=0bd47f9c-cf6a-47e9-bd24-cdaf7cab38f5 none swap sw 0 0
[/FONT]
```
to:
```
[FONT="Courier New"]# /dev/sda7
/dev/sda7 none swap sw 0 0[/FONT]
```

[/EDIT]

Oh yeah, and change the root= kernel param to point to the new root partition, I forgot all about that (and you even posted menu.lst and everything!).

---

### Post by alyson on 2007-01-11
Yes!  It worked!  I'm posting this from my newly-expanded Ubuntu partition.  Ubuntu and Windows both boot without a hitch now, and I finally learned a few things about GRUB (of which I'm now somewhat less terrified).  Thank you, thank you, thank you, po0f!  I wish I could bake you cookies or a cake or something.  I mean, you spent well over an hour of your time helping me; I don't think I've been nearly as helpful to anybody for some time now.  So thank you.

---

### Post by po0f on 2007-01-11
alyson,

Don't sweat it.  Cookies *are* tasty though...

Are you able to get your new partition mounted and everything?

---

### Post by alyson on 2007-01-11
Yeah, everything seems to be fine so far.  I do have one question, though.  If--and I certainly won't do this now--I want to merge the two random, tiny ext3 partitions (which, as far as I can tell, don't serve any purpose) into my Ubuntu partition, is that possible?  And if it is, will I have to go through this again?  I mean, I guess it doesn't really make a difference--I just *know* they're there, and it bugs me, like a crooked picture.  Maybe I can just wait until I do a fresh install of Feisty.

---

### Post by po0f on 2007-01-11
alyson,

Merging partitions together is something I haven't attempted yet.  I'd sooner spring for a backup/fresh install than try something like that.  /dev/sda7 doesn't look to be of use for anything, and /dev/sda5 doesn't seem to sizable either.  For now, I wouldn't worry about it.  ;)

---

### Post by alyson on 2007-01-11
Yeah.  I guess I'll live.  Thanks again, po0f.

---

