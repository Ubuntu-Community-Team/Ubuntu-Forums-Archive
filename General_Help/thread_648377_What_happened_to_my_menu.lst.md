---
title: "What happened to my menu.lst?"
date: 2007-12-23
forum: General Help
---

### Post by kachofool on 2007-12-23
After installing system updates yesterday, Grub's menu.lst reverted to its default. What's up? Are the two related? I haven't installed/uninstalled anything except for those updates. Can I get my old menu.lst file back? I had it config'd pretty nicely... sort of pissed that it just disappeared. I'm using Gutsy btw

---

### Post by oscarsfriend on 2007-12-23
If there was a kernel update then it probably wrote over your menu.lst.  However, there should be a backup called (I think) "/boot/grub/menu.lst~" (note the ~).

---

### Post by ~LoKe on 2007-12-23
Yep, you'll have to restore a backup.

There are certain lines you can modify in menu.lst that will apply to all new kernels.  Like for me, I have quite and splash removed for all my kernels, and when I install a new one, it's removed for it as well.

---

### Post by kachofool on 2007-12-23
The backup is the exact same as the normal menu.lst. Quick side-question, what the hell is 'chainloader +1'. I read the GRUB manual and tried searching for it on this forum but came up with some pretty bad explanations.

---

### Post by oscarsfriend on 2007-12-23
Sorry I don't know about the chainloader thing.  I know this is too late now, but I always keep my own backup of things like menu.lst, and xorg.conf.  When I'm sure I have one that works, I make a copy of it with a name like menu.lst_safe, and xorg.conf_safe.  This way the backups won't get accidentally written over.  Also, I believe there is a way to stop the updater interfering with certain files.  Take a look at [this thread](http://ubuntuforums.org/showthread.php?t=369596&highlight=dpkg-divert). (Skip down the first post to after the images. I've hilighted the text in red.)

---

### Post by kachofool on 2007-12-23
Thanks for the tip.

I don't know exactly what that update did, but I can't access my recovery partition anymore. I have my grub setup like so...

(hd0,0) -> IBM Recovery partition
(hd0,1) -> Vista
(hd0,2) -> media partition (non bootable)
(hd0,3) -> Ubuntu

But both (hd0,0) and (hd0,1) boot to Vista now. I don't know what to do... 
fdisk shows 6 partitions,
dev/sda1 :: unknown system type (I'm guessing this is the recovery partition)
dev/sda2 :: HPFS/NTFS, bootable (guessing this is Vista)
dev/sda3 :: W95 Ext'd (LBA)...I have no idea what this is, maybe my media partition
dev/sda4 :: Linux
dev/sda5 :: HPFS/NTFS, no idea what this is
dev/sda6 :: Linux swap

fdisk also tells me that sda1,2,3,4 do not end on cylinder boundary. No idea what that means either. Any ideas where I go from here? ... I'm pretty fed up with this.

---

### Post by oscarsfriend on 2007-12-23
I have something similar that happens on my hp pavilion machine.  It is dual booting (two hard drives, one kubuntu, one XP with a recovery partition).  My other machine is fine after kernal updates, but all the Windows information is removed from menu.lst on my pavilion.  Which is why I back it up.  This is the section from mine:

```

title           Microsoft Windows XP Home Edition
root            (hd1,1)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Note the last three lines.  I think this is something to do with switching the two windows partitions (XP and recovery) around so that you don't boot into the recovery partition, which will reinstall Windows, and wipe all your data.  Not much help, I expect, but it might get you started.

EDIT: From [here](http://forums.fedoraforum.org/showthread.php?t=145424): "chainloader +1 : This command will take the boot sector of the root and use it to boot. If the root in a whole disk, then it will load the MBR."

---

### Post by kachofool on 2007-12-23
Hmmm.... just reading the last three lines and trying to understand it...
I'm guessing when you map hd0 as hd1, "hd0" is identified as "hd1", and the second line makes the opposite true. So when you specify root: hd0, it's actually hd1, and vice versa... 

I think this only applies to dual hard drive machines... since hd0 refers to one physical hd and hd1 refers to another one.

The chainloader thing I think has to do with the fact you're 'chain-bootloading' since you use GRUB initially and then GRUB calls NTLDR (another bootloader) for XP. So maybe that means chainload +1, since its GRUB->NTLDR... not really sure how chainloader +2 would work or what it means though!

In any case, thanks for your help... but I'm think that in this case, I can't use the map(hd0,hd1) thing =p

---

### Post by logos34 on 2007-12-23
> **kachofool said:**
> ...hd0, it's actually hd1, and vice versa... 

I think this only applies to dual hard drive machines... since hd0 refers to one physical hd and hd1 refers to another one.

Yes, that's correct, it doesn't apply in your case because you're not trying to boot windows on another hard disk.
> 
I don't know exactly what that update did, but I can't access my recovery partition anymore.

Are you trying to boot the recovery partition from grub or has it stopped mounting in linux?

---

### Post by kachofool on 2007-12-23
It mounts in Linux, but when I try to actually boot it through GRUB, it just boots Vista instead.
To clarify, booting
root: (hd0,1) and
root: (hd0,0)

do the exact same thing

---

### Post by logos34 on 2007-12-23
then it appears the vista boot manager/bootloader is on the bootsector of the recovery partition.  Perhaps the only way to boot the recovery is to use the vista bootloader.  Not sure.  But if you have to do that, you can still boot ubuntu--just use EasyBCD to add linux entry and reinstall grub to ubuntu root partition.

But you were able to before the update, right?

---

### Post by kachofool on 2007-12-23
I can access both Vista and ubuntu through GRUB. After the update however, I can't access my recovery partition, and before I was able to access it.

---

### Post by rbmorse on 2007-12-24
Is the recover partition still in the partition table? Is it shown when you run gparted or (from a terminal window):

sudo fdisk -l   (where the "l" is a lower case letter "L")?

---

