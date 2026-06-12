---
title: "Dual boot with Vista."
date: 2008-06-09
forum: General Help
---

### Post by Rafal07BC on 2008-06-09
Hello.

I have been looking for answer to my problem for few days now but with no effect.
I hope you can help me with my problem.

This is how my disk is partitioned:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  82  Linux swap / Solaris
/dev/sda2             785        6006    41945715   83  Linux
/dev/sda3   *        6007       11228    41945715    7  HPFS/NTFS
/dev/sda4           11229       60801   398195122+   f  W95 Ext'd (LBA)
/dev/sda5           11229       37337   209720511    7  HPFS/NTFS
/dev/sda6           37338       60801   188474548+   7  HPFS/NTFS

```

Before I installed Ubuntu I had installed Windows XP on sda2. I used sda1 as swap partition. Then I installed Vista on sda3.
After playing for a while with Ubuntu in virtual environment I decided to switch to it.
As you can see I decided to remove XP and use sda1 as linux swap and sda2 as linux partition.
All went well and I am using Xubuntu as my default os but I also do need to use Vista.

Xubuntu installer didnt add entry for Vista to grub.

I tried to do it myselt, but to no effect. This is how menu.lst file looks like right now.

```


title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=02df2b3d-86b0-4edc-bfba-45c5a5f8fa05 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title		Vista
root		(hd0,2)
makeactive
chainloader	+1

```

With such setup I get cant find BOOTMGR message when I try to run Vista.

Could you please advise me how to configure grub so I can start Vista in current setup?

Thanks in advance.

---

### Post by meierfra. on 2008-06-09
Grub is already configured correctly. But the booting information for Vista was an the XP partition you deleted. This [link]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") should help you fix the problem.

After you fixed your Vista problem, you will have to reinstall grub. Boot from the LiveCD, open a terminal and type:

```
sudo grub
```

and at the grub prompt:

```
root (hd0,1)
setup (hd0)
quit
```


Finally you need to move your vista item below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

This does not help with your booting problems, but otherwise Vista will disappear from your Grub Menu during the next kernel update.

---

### Post by didac on 2008-06-09
Seems correct. Maybe the only thing needed is to add a blank line after the chainloader.

---

### Post by Rafal07BC on 2008-06-09
Thanks meierfra.
Worked like a charm. 
I event didn't have to reinstall grub.
Fixing vista install was enough.

---

