---
title: "major problems upgrading from breezy to dapper"
date: 2007-01-29
forum: General Help
---

### Post by rajan on 2007-01-29
Hi all, I tried to upgrade my desktop to dapper because I was having a whale of a time trying to get yahoo to stop crashing my firefox applications. I did the normal change repository, then update, then upgrade, but after about 10 minutes the system went down for a halt that looked like it was unexpected. when it restarted, X wouldn't start up (actually it makes my monitor turn off and on 2-3 times) because it couldn't find the keyboard and it said something like this:

"the x server is now disabled. Restart GDM when it is configured correctly."

and in a different place it says at the end of a big error message:

no input driver matching 'mouse'
no core keyboard
fatal server error
failed to initialize core devices

and now I can't get to my system. Even the virtual terminals or whatever it is that you get to by hitting cntrl+alt+f1 is not working so i can't alter anything. If you have any leads on this problem, I'd really appreciate it. 

However, my real question is regarding a regression to breezy. if nobody has any clues for the above problem, i will reinstall breezy from my CD. However, I really really don't want to lose any of the data files that I had in my ~/home directory. How can I do this? I had an LVM partition before, and when I went partially through the installation procedure (stopped right before I repartitioned), the partition manager found the previous partition.

also, what is the "resize partition?" does that just truncate the size of the partition to only the used areas, or is it more randomly cut than that?

---

### Post by rajan on 2007-01-29
I think this thread will help me out, but if you have any other ideas, i'm all ears. 

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

it'll have to wait until tomorrow though. i have the feeling that when i figure this out, i'll have built a lot of "character"

:mad:

---

### Post by hal10000 on 2007-01-29
This is a guide for upgrading from breezy to dapper: [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by rajan on 2007-01-29
yeah i saw that, but i don't see anything that would help me fix my system.

anyone?

---

### Post by hal10000 on 2007-01-29
I guess you just have to reconfigure your xserver: [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg [/COLOR]

If you have an ATI or NVIDIA graphic card and want to have 3D hardware accelerated grapgics you might first (re)install the restricted modules package:
[COLOR="Red"]sudo apt-get install linux-restricted-modules-$(uname -r)[/COLOR] (and for nvidia cards additionally[COLOR="Red"] sudo apt-get install nvidia-glx[/COLOR]

---

### Post by rajan on 2007-01-29
right but i can't get to a terminal or anything like that where i could actually change any files. any suggestions?

---

### Post by hal10000 on 2007-01-30
You should be able to log into a console: Press <CTRL>+<ALT>+<F1> simultaneously, then log in to the console.

---

### Post by rajan on 2007-01-30
yeah for some reason that doesn't work either. i remember having problems with that previously, but it doesn't give me a prompt now. it simply flashes a white cursor on the black screen. i can type, but my commands don't have any response. 

i believe i'll have to use the live CD thing and completely reinstall. thanks for your help, Hal.

---

### Post by igknighted on 2007-01-30
Can you boot into recovery mode?  Or, before you reinstall, try looking up how to chroot into your install from the live CD.  Both of these could solve your problem.

---

### Post by rajan on 2007-01-30
when i try to boot into the recovery mode (from grub, i am assuming), i don't get anything except the system trying to boot from a CD or floppy. i'll have to try the chroot thing. thanks for the tip!

---

### Post by igknighted on 2007-01-30
actually, much easier, just thought of this... mount your Ubuntu drive while on the live CD then try to edit the /etc/X11/xorg.conf file.  Go to section "device" and change the driver to "nv" if using nvidia or "ati" if using an ATI card.  Then save it and try to boot ubuntu.

---

### Post by rajan on 2007-01-30
isn't the live CD session "read only"? can i save changes on the HD through the live CD?

---

### Post by hal10000 on 2007-01-30
It's not read-oly if you mount it with the sudo command

---

### Post by rajan on 2007-01-30
excellent! thanks again, guys. I will be implementing these over the next few days, but for now i need sleep. :D

---

### Post by rajan on 2007-01-31
Back again.... So i'm able to use my computer again but only in the live CD capacity. I tried to reconfigure the xserver, but it didn't work and i think i only reconfigured the xserver for the live CD session. i'm assuming  that i do, indeed need to access my old filesystem and make the changes there. however in order to mount a drive like that, i first have to know where it is, then i should probably add that entry into the fstab file and then finally i should mount it in the correct place. if you have any hints for any of these steps, i'd really appreciate hearing them. on a side note, when i was searching for the man pages for "mount," i searched "man mount" and shockingly i didn't find any of the pages that i feared i would... just wholesome linux pages!!

---

### Post by hal10000 on 2007-01-31
First boot your live cd, then you have to find out where your ubuntu partition resides: open a terminal window and do [COLOR="Red"]sudo fdisk -l[/COLOR] 
This will show you all partitions on all harddisks, similar to this:
```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         892     7164958+   7  HPFS/NTFS
/dev/hda2             893        1866     7823655   83  Linux
/dev/hda3            1867        2840     7823655   83  Linux
/dev/hda4            2841        4865    16265812+   f  W95 Ext'd (LBA)
/dev/hda5            2841        4802    15759733+  83  Linux
/dev/hda6            4803        4865      506016   82  Linux swap / Solaris

Disk /dev/hdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        5222    41945683+  83  Linux
/dev/hdd2            5223       10011    38467642+   5  Extended
/dev/hdd5            5223       10011    38467611   83  Linux

```
In the example you can see two harddrives /dev/hda and /dev/hdd with some partitions in each of them. I know that my ubuntu resides in /dev/hda5, but in case you dont' know where your ubuntu lives, you may have to mount them all and browse through to find e.g. files in your /home directory (assume that your /home resides in your system root (/) ).

You can mount a partition with: [COLOR="Red"]sudo mount /dev/hda5 /mnt[/COLOR], then browse through the mountpoint-directory (in this example /mnt and find out wether it is your ubuntu system or not.

To unmount the partition use [COLOR="Red"]sudo umount /mnt[/COLOR] (NOTE: umount without an n)

Once you found your ubuntu system, mount it.
In the example code i assume /dev/hda5 is your ubuntu-system, change it to your needs.

 [COLOR="Red"]sudo mount /dev/hda5 /mnt[/COLOR]

Next step is to reconfigure your xserver (like you mentioned above, for the live CD session): [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

Once you've made your changes and stored them to /etc/X11/xorg.conf, restart your xserver to verify your settings are correct
NOTE: DON'T REBOOT OR YOUR CHANGES WILL BE LOST(i guess there is a menu entry to restart the xsession).

If it works and you can login to gnome again, then your xsever now runs correct.

Now back to the (previosly) mounted ubuntu system on your harddrive:
First backup the existing xorg.conf on your ubuntu system partition:
[COLOR="Red"]sudo cp -a /mnt/etc/X11/xorg.conf /mnt/X11/xorg.conf.backup[/COLOR]

Then just copy the xorg.conf from your ubuntu CD session to your ubuntu partition on your harddrive:
[COLOR="Red"]sudo cp /etc/X11/xorg.conf /mnt/etc/X11[/COLOR]

Second last step is to unmount the ubuntu partition:
[COLOR="Red"]sudo umount /mnt[/COLOR]

Last, not least: reboot to your ubuntu system

Very last step: (hope you) enjoy

---

### Post by rajan on 2007-01-31
thanks a lot Hal. I am having a hard time finding my ubuntu files. i think i have a very similar HD to your hdd. I have a hda1, Linux; a hda2 Extended; and an hda5 Linux LVM. when i try to mount the hda5, i get a message that says " mount: /dev/hda5 already mounted or /mnt busy" and when i try to mount the hda2, it says "you must specify the filesystem type"

do you have any guesses on how to get around this? i haven't mounted the disk before i tried to get it to mount just now. thanks again.

and using sudo mount -t ext3 /dev/hda2 /mnt doesn't work either because the it's the "wrong type, bad option, bad superblock on /dev/hda2, missing codepage or other error"



by the way, i really think it's my keyboard/mouse because that's the only issues that have been showing up on the messages upon xserver failure. i can't see how they would affect the xserver, but i've seen stranger things.

---

### Post by rajan on 2007-01-31
output from sudo fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        4865    38829105    5  Extended
/dev/hda5              32        4865    38829073+  8e  Linux LVM
ubuntu@ubuntu:~$

```

and......
output from dmesg | tail

```

[17180173.444000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180173.444000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17180173.444000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17180173.732000] [drm] Setting GART location based on new memory map
[17180173.732000] [drm] Loading R300 Microcode
[17180173.732000] [drm] writeback test succeeded in 1 usecs
[17180613.564000] SQUASHFS error: Can't find a SQUASHFS superblock on hda2
[17180690.836000] attempt to access beyond end of device
[17180690.836000] hda2: rw=0, want=4, limit=2
[17180690.836000] EXT3-fs: unable to read superblock

```

so that pretty much means my EXT3 is toasted?

---

### Post by hal10000 on 2007-01-31
Please post the content of your /etc/fstab file FROM YOUR UBUNTU SYTEM (not the one from your live CD)

In many cases, even if the partition is somehow damaged you can restore it with the fsck command.
You may use (from your live CD WITH /dev//hda2 UNMOUNTED) [COLOR="Red"]sudo fsck.ext3 -f /dev/hda2[/COLOR]

I'm not very used to LVM, so to help you further i first have to look for LVM fuctionality by myself.

---

### Post by rajan on 2007-01-31
this is the only fstab i can get to because of my previous problems mounting hda5. i have tried unmounting /mnt, unmounting /dev/hda5, and then remounting via ```
 sudo mount /dev/hda5 /mnt 
``` but it still doesn't work.

so here's the fstab (almost certainly this is the one from the CDROM)
```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

this is what i get when i try "sudo umount /mnt"
```

umount: /mnt: not mounted

```

even if i have just tried to mount something

and this is what i get when i try "sudo fsck.ext3 -f /dev/hda2"
```

ubuntu@ubuntu:/etc$ sudo fsck.ext3 -f /dev/hda2
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2
Could this be a zero-length partition?
ubuntu@ubuntu:/etc$

```


thanks again Hal.

---

### Post by rajan on 2007-02-01
i have now learned that according to gparted, the filesystem on the part of the partition that has most of my data is bad. does anyone have any hints on how to recover it? it's gonna cost me a lot of money to get it repaired professionally.

---

### Post by hal10000 on 2007-02-02
your /dev/hda5 is a LVM partition, which is a special kind of partition. As i told before, i'm not very used to LVM and at the moment i don't have enough time to make any effords towards this, so i'm sorry if you feel let alone with your problems.

But i can say that professional service to repair a harddrive can be very expensive.
There are some tools you might try first by yourself e.g. a program called [COLOR="Red"]testdisk[/COLOR], a data recovery tool which helped me many times. It's a commandline tool, but it's relative easy to handle.
I hope in a few days I'll have more time.

---

### Post by rajan on 2007-02-02
Hey Hal,
i have a feeling that i'll have to rebuild the filesystem and this is possibly not going to work. so i am going to use testdisk before i try that. i think they are the last, and second-to-last options, respectively. don't worry about taking too much of your time up with this. i think by sunday i will reformat my HD with a completely new install of dapper because i need my computer more than i need my data at this point. have a good night, and thanks a lot,

rajan

---

