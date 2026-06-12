---
title: "[SOLVED] GRUB Updating"
date: 2007-12-12
forum: General Help
---

### Post by fjgaude on 2007-12-12
Okay, I have a triple boot Ubuntu box that boots from /dev/sda2, a partition I don't wish to use anymore.

I also have partitions /dev/sda3 and /dev/sda5 that are 32- and 64-bit that I still use. I wish now to boot from the sda5 partition.

Question: what do I put in the groot= and kopt= portions of the menu.lst file, and which one in sda2 or sda5, before I use update-grub command?

If someone has a ready for-sure answer it will save me from making mistakes. Thanks.

---

### Post by logos34 on 2007-12-12
> **fjgaude said:**
> Okay, I have a triple boot Ubuntu box that boots from /dev/sda2, a partition I don't wish to use anymore.

I also have partitions /dev/sda3 and /dev/sda5 that are 32- and 64-bit that I still use. I wish now to boot from the sda5 partition.

Question: what do I put in the groot= and kopt= portions of the menu.lst file, and which one in sda2 or sda5, before I use update-grub command?

If someone has a ready for-sure answer it will save me from making mistakes. Thanks.

Boot into x64 ubuntu and reinstall grub to mbr pointing to that partition (sda5).  You shouldn't have to change anything on groot or kopt lines--groot should point to sda5 (i.e. 'hd0,4') and kopt= the same uuid.

sudo grub-install /dev/sda

---

### Post by fjgaude on 2007-12-12
Thanks for the quick reply... if you hear a loud yell coming from the area you know something: I failed or I had success. <smile>

---

### Post by fjgaude on 2007-12-12
Okay, I did as you suggested, and I'm still booting from sda2, not sda5. Don't I need to use update-grub?

Is there something else we are missing?

---

### Post by logos34 on 2007-12-12
ok, then try

sudo grub
>root (hd0,4)
>setup (hd0)
>quit

---

### Post by fjgaude on 2007-12-12
> **logos34 said:**
> ok, then try

sudo grub
>root (hd0,4)
>setup (hd0)
>quit

I thought for sure that would do it, but it didn't. Still using the sda2 menu.lst menu. Hmmm...

---

### Post by logos34 on 2007-12-12
wtf? something's screwy...if x64 is sda5, and that's the one you want grub on the mbr to point to, then the command I just gave you should work, even if you're on another partition.  You're telling it to write grub to the mbr pointing to the menu.lst on sda5.  Why is it still pulling up sda2 mneu.lst?  Run it again and post the output.  Post **sudo fdisk -l** too whule you're at it.
AND both your menu.lst's (let's get to the bottom of this).

---

### Post by fjgaude on 2007-12-12
Okay, I've run the various commands several times and I still get the menu.lst that is on sba2, but I'm actually booting from sda5 as shown by fdisk -l:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f048f04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         389     3124611   82  Linux swap / Solaris
/dev/sda2             390       11988    93168967+  83  Linux
/dev/sda3           11989       24858   103378275   83  Linux
/dev/sda4           24859       38913   112896787+   5  Extended
/dev/sda5   *       24859       38336   108262003+  83  Linux
/dev/sda6           38337       38913     4634721   82  Linux swap / Solaris
```

The little star points to the boot partition, right? Yes.

Funny, there is still something telling grub to go to sda2 and show the menu.lst there.

---

### Post by logos34 on 2007-12-12
The asterisk is the boot flag indicating the current active partition.  But that's not causing a problem here.

Can you post your menu.lsts?  And did you get any errors when you ran 'setup'?

---

### Post by fjgaude on 2007-12-12
Okay again... Ubuntu is going to make a Linux expert out of me one way or the other.

I have a four drive setup with three of them used in a raid5 array. Here's the full fdisk-l output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f048f04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         389     3124611   82  Linux swap / Solaris
/dev/sda2             390       11988    93168967+  83  Linux
/dev/sda3           11989       24858   103378275   83  Linux
/dev/sda4           24859       38913   112896787+   5  Extended
/dev/sda5   *       24859       38336   108262003+  83  Linux
/dev/sda6           38337       38913     4634721   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000065b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dc58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       36481   293033601   fd  Linux raid autodetect

Disk /dev/md32: 600.1 GB, 600132681728 bytes
2 heads, 4 sectors/track, 146516768 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md32 doesn't contain a valid partition table
```

Now going to the sda2 menu.lst, the part we are interested in shows that we somehow think the boot drive is /dev/sdd:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic (64-bit sda5)
root		(hd3,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=56c46aaa-13fc-4247-8d65-d979b56c5188 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic quiet
```

Notice the root as (hd3,4). Now this has to do with Linux not being sure what UUID or partition name to use? Gosh...

No errors when running setup.

---

### Post by fjgaude on 2007-12-12
What if I took those stars (boot) out of the raid drives?

---

### Post by logos34 on 2007-12-12
WHY didn't you say at the very beginning you had more than one drive, let alone a RAID array???

Jeez...

In the future you need to make clear your setup.

The 'root (3,4)' in the menu.lst means that sda5 is being seen as the fifth partition on the **fourth** (not first) disk...But apparently grub is on one of the raid array drives.  You're booting  from one of those

So try 

sudo grub

>find /boot/grub/stage1
(should return among other things '(hd3,4)')
>root (hd3,4)
then try setup hd0-3 untill you find one that works.

>setup (hd0)
>quit

or 
>setup (hd1)

etc.

---

### Post by fjgaude on 2007-12-12
Sorry about not being complete at first... didn't think it would matter, but now I know that it does. Thanks for being patient with me.

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
 (hd0,2)
 (hd0,4)

grub> root (hd3,4)
root (hd3,4)
Error 22: No such partition

grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)       
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
```

Now I'll reboot and get back with you, success or failure. <smile>

---

### Post by fjgaude on 2007-12-12
Didn't work... I did take the boot stars out of the three raid5 drives.

I could stop the raid, their controller, and see what happens then. I do have the BIOS pointing to the sda drive. It is 320G while the other three are 300G.

---

### Post by logos34 on 2007-12-12
> grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,1)
 (hd0,2)
** (hd0,4)**

> I do have the BIOS pointing to the sda drive.

ooookay, so I guess it is hd0,4 after all.  (but apparently is was in fourth place at the time of install).  

If the 320 gb sda is first in the bios hard disk boot order, then 

> root (hd0,4)
grub> setup (hd0)

ought to work.

yep, stop the raid or disconnect them entirely.  Then it should boot correctly.  But you need to find a way for this to work with the raid array.  I don't know what the problem is.  (and you tried deleting the raid boot flags) I have no experience with raid so someone else will have to help you from here.

---

### Post by logos34 on 2007-12-12
make sure to change sda5 menu.lst 'groot' and root lines from (hd3,4) to (hd0,4)

gksudo gedit /media/sda5/boot/grub/menu.lst (or whatever the path is)

---

### Post by fjgaude on 2007-12-12
Okay, man... it's working as it should.

What I did was disengage the raid controller on the MB, rebooted, and I was on sda5's grub boot menu. Ran fine without the raid, but all my data, pictures, artwork is there. So, I rebooted and engaged the raid controller, and, and... it worked.

Seems the kernel has some kind of memory as to what was first drive or something. To my memory I never used any of the 300G drives to boot. Early on, in Edgy, I had trouble consistently booting because of drive name switched, but in Gutsy that went away. Many changes have been going on in the kernel to handle changes in multidrive systems, like adding one and not having the names change.

So, thank you for leading me to the solution with grub... from now on, I am closer to becoming an expert than I care to. <grin>

Peace.

---

### Post by logos34 on 2007-12-12
> **fjgaude said:**
> Okay, man... it's working as it should.

What I did was disengage the raid controller on the MB, rebooted, and I was on sda5's grub boot menu. Ran fine without the raid, but all my data, pictures, artwork is there. So, I rebooted and engaged the raid controller, and, and... it worked.

Seems the kernel has some kind of memory as to what was first drive or something. To my memory I never used any of the 300G drives to boot. Early on, in Edgy, I had trouble consistently booting because of drive name switched, but in Gutsy that went away. Many changes have been going on in the kernel to handle changes in multidrive systems, like adding one and not having the names change.

So, thank you for leading me to the solution with grub... from now on, I am closer to becoming an expert than I care to. <grin>

Peace.

Well whatya know. Glad that's solved.  Didn't have much confidence in a happy ending.  Thought you'd be back to square one as soon as you reconnected the raid.  

I'm kind of surprised you were having trouble with musical drive names since edgy, because edgy was the first release to use the UUIDs, which was adopted in part to address precisely such issues (multiple drives on different sata controllers).

Anyway, peace to you too,  happy holidays and enjoy ubuntu x64.  That's what I run now (ubuntu studio) and no major problems (but some annoying small ones!)


add: I just wish I'd have included the 'find' part of the grub command the first time--it would have saved some confusion by alerting us to the discrepancy with sda5 menu.lst (hd0,4 vs. hd3.4)

---

### Post by fjgaude on 2007-12-12
Yes, life is good. You may not know it but I've been using Linux since 1996, early Red Hat. Being a graphic design I try to not know too much about the OS and such. Visual design is where I like to spend most of my thought and intuition.

> add: I just wish I'd have included the 'find' part of the grub command the first time--it would have saved some confusion by alerting us to the discrepancy with sda5 menu.lst (hd0,4 vs. hd3.4)

You know I don't think it would have... it thought that hd3,4 didn't exist. Anyway, I believe that the kernel places on disk some lines to remember certain things, like drive names vs UUIDs. And it was something like that that caused my unusual problem.

Happy Holidays, and keep clean and dry.

And thanks again for everything.

---

