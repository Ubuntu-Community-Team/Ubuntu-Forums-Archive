---
title: "Please Help..I hosed Grub"
date: 2008-07-09
forum: General Help
---

### Post by ericnord on 2008-07-09
Hey everyone,

I had my system working just fine w/ Ubuntu, Vista, and XP triple booting. I would boot to Grub which would allow me to boot to Ubuntu or Vista bootloader. Vista bootloader would then allow me to boot to Vista or XP.

I had 4 partitions on my first hardrive:
1. Vista
2. XP
3. Ubuntu
4. Misc NTFS

I wanted a clean install of Ubuntu so today I ran partition magic from DOs and removed partition 3 above and resized 4 to take up the new space. I made a new partition on a seperate HD for Linux. So now the first HD just has:
1.Vista
2.XP
3. Misc NTFS

Now when I boot I get no Grub. When I boot w/ LiveCD it says can't access tty so it won't load.

I'm assuming I need to put Grub back on, but do I put it on the first HD or the HD that will have linux? How do I re-install grub and also add the Vista Bootloader entry back in?

If I lose my XP OS I'm screwed!

All my fault I know...

Thanks

---

### Post by Activist on 2008-07-09
"can't access tty so it won't load."
tty?

after the resizing of partitions u reinstalled ubuntu on partition? (i dont get the fourth drive, 4th partition maybe)

---

### Post by VMC on 2008-07-09
> **Activist said:**
> "can't access tty so it won't load."
tty?

after the resizing of partitions u reinstalled ubuntu on partition? (i dont get the fourth drive, 4th partition maybe)

I think he means this:

Before:
> 1. Vista
2. XP
3. Ubuntu
4. Misc NTFS
Now:
> 1. Vista
2. XP
3. Misc NTFS
4. Ubuntu (or will be)

ericnord,
Have you ever booted up using the Livecd before? Also, when you boot up normal, what error message do you get.

---

### Post by rraj.be on 2008-07-09
Its better to install GRUB on your fourth partition.
To reinstall GRUB do the following
```

Boot into your livve cd

open the terminal
```

type
```

sudo grub

find /boot/grub/stage1
```

if it returned like ```
root(hd0,0)
```

then type 
```

root (hd0,0)

setup (hd0,0)

quit

sudo reboot
```

That's it.

---

### Post by Cap'n Skyler on 2008-07-09
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
it is a great tool and you will soon be grand master of Grub!!
get the ISO and burn to cd,and re boot :):popcorn:

---

### Post by ericnord on 2008-07-09
Sorry everyone for the confusion. I have 4 hardrives and moved Ubuntu to the fourth HD. So first HD just has 3 partitions now.

I have the SuperGrub ISO, but can't find how to manually see the grub code. It has all these steps to fix things, but none are working.

I'll update the first post to avoid further confusion.

I have booted w/ LiveCD in the past, that is how I did first install.

Error I get now is, "Grub loading, please wait... Error22"

---

### Post by logos34 on 2008-07-09
Reinstall grub to the mbr of the boot drive, from the live cd as _rraj.be _suggested, but like this:

> sudo grub

grub> find /boot/grub/stage1
(enter output next command)
grub> root (hd?,?)
grub> setup (hd**0**) -->you want it to overwrite the existing grub so it points to new ubuntu location
grub> quit

Hopefully it will have the correct boot entries for windows

---

### Post by cariboo on 2008-07-09
Your best bet would be to repair the Vista boot loader first and then you can install Ubuntu. When you deleted the Ubuntu partition you also deleted grub, all thats left is grub in the mbr. You should repair your mbr so that Vista and Xp will boot first, then install Ubuntu.

Jim

---

### Post by logos34 on 2008-07-09
oh, so he hasn't actually done a fresh install yet, I see...
> 
but do I put it on the first HD or the HD **that will have linux**? 

But I think restoring the vista/windows bootloader is unecessary, IMO...just go ahead and do the fresh install of ubuntu and hopefully it overwrite the existing grub on the boot disk, as well as detect vista and add menu.lst entry

---

### Post by ericnord on 2008-07-10
Hey everyone,

Thanks for the help! I got it working. Here are the steps I had to do:

1. Boot to VistaCD and do bootrec / FixBoot
2. Then do bootrec / FixMBR
3. Then I could boot to the LiveCD

Thanks

---

