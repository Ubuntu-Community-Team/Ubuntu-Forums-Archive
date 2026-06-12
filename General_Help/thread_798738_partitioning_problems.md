---
title: "partitioning problems"
date: 2008-05-18
forum: General Help
---

### Post by torik92 on 2008-05-18
I wasn't sure where to post this, so I posted it in General Help..

I have a Dell inspiron 1525, with Vista pre-installed. Recently I have installed Ubuntu, I installed it on the existing 10GB backup drive because I was going to replace vista with XP anyway. I wasn't able to create a swap partition though, because there were already four partitions (one of them was extended,whit another one inside it (a Dell Media Direct partition), but I didn't know what extended partitions were then.) I didn't know I couldn't have more than four partitions so I shrunk the Ubuntu partition by about 2GB and planned to fill the space with a swap partition, but obviously that didn't work.

Later I got some problems with overlapping partitions (I'm not sure how that happened) and gparted didn't even recognize any of my partitions at one point. I found out that it was the dell media direct extended partition that was overlapping the vista one, and was able to delete the whole extended partition using fdisk. After that gparted recognized my partitions as usual.

I was going to do some more partitioning (make a data partition and a swap partition and fill the unallocated space i had left) so I downloaded the gparted live CD and burnt it to a disk, but when I try to boot it up it just show some weird error message after it starts trying to mount root:

"**interleaved files not (yet) supported**"

and underneath: "! = 0" or something... 

So, _what does interleaved files mean??_ :confused:

Is it something bad?

I did manage to make a data partition and a swap partition under an extended one using gparted under ubuntu, but I also want to resize my ubuntu partition, and I don't want my HDD to contain any errors... 


Oh! And I almost forgot: When I try booting with the XP installation CD it says it can't find any Hard Drives...
Don't know if that is relevant or if it is a separate issue though.

Here's my current partition-table:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        1046     8305605   83  Linux
/dev/sda3   *        1318       16582   122606717+   7  HPFS/NTFS
/dev/sda4           16583       19457    23093437+   5  Extended
/dev/sda5           16583       16773     1534176   82  Linux swap / Solaris
/dev/sda6           16774       19457    21559198+   b  W95 FAT32

All help will be greatly appreciated!

---

### Post by torik92 on 2008-05-18
BUMP... :roll: 
Seriously, I can't find any information about this anywhere.
I need some help

---

### Post by torik92 on 2008-05-19
$_ sudo help me ?

---

### Post by yogithebear73 on 2008-05-19
Um... I could be wrong, but sounds like you messed up your partition table. Try searching for a way/program to repair partition tables...i hear it takes a really long time though, just so you know. it has to scan your entire hd and redo your table.

Wait a couple of days to see what other people say.

---

### Post by vikrant82 on 2008-05-19
> When I try booting with the XP installation CD it says it can't find any Hard Drives....

That is because the XP cd you are using doesn't have the the drivers needed for your hard disk connector, which is probably set up at anything other than ATA. Try checking BIOS, I remember a friend, who has similar problem (XP not detecting HD), when changed the hard disk mode from BIOS was able to install XP. Its a dell specific issue.

I have had some troubles with gparted myself. Try booting your PC with a Hiren's boot cd or Hiren's bootable USB.
- Unmark third partition as boot partition. [It might complain that there are no active partitions, let it.. ]
- Change HD drivers from BIOS, install XP.
- In your setup, I'd also delete the logical drives and then extended partition for now and recreate them afterwards.
- Install XP and then go ahead with ubuntu.

Keep us posted how it goes.

---

### Post by torik92 on 2008-05-19
Thanks, changing drivers to ATA worked.
I at least got XP installed, although I can't find any drivers for my network card, only vista drivers :(
But now my computer doesn't load grub at startup, it only boots straight into windows and I can't access ubuntu anymore, how can I fix that?

And the gparted live cd still doesn't work, the full error message I get is: 
> Interleaved files not (yet) supported
file unit size != 0 for ISO file (2240)
Anyone know what that might mean?

I haven't tried that boot cd you suggested yet, did you mean I could use it for partitioning instead of gparted?

I also didn't remove the logical partitions because I have some downloaded files and stuff in there that i didn't want to lose and I didn't have anywhere else to put it.

If anyone know anything about windows wireless drivers I would also appreciate some tips about that.

Edit: Nevermind, I found the XP drivers :)

---

### Post by torik92 on 2008-05-20
I can access my ubuntu partition from the ubuntu install cd, that might probably help... Don't know what to do though... :confused:

---

### Post by black drongo on 2008-06-01
u can fix it from live cd. this link may be of help(if u haven't already fixed this)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28install%29%7C%28windows%29)

---

### Post by torik92 on 2008-06-08
Thanks man :cool:
I'm back on my Ubuntu system now :D

I have also set up the partitions using gparted from the installaton cd.
The only thing I want to know now is what the error message from the gparted live cd means... like I said; I don't want my partitioning table to contain any errors

---

