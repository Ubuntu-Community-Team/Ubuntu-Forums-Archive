---
title: "Help adding Windows to Grub"
date: 2008-03-31
forum: General Help
---

### Post by uberlube on 2008-03-31
Hey guys. So i recently added windows to a small partition I have and I didnt quite read into it enough before I did because it wiped out my grub. I grabbed Super Grub Disk and restored my Linux boot (although it gives me a filesystem error and dumps me into a command line. Entering 'exit' brings me to my login window and desktop so Im not to worried about that at this point.) But now I need to add windows manually to my menu.lst. I tried adding this:

```
title Windows
root (hd0,1)
chainloader +1
```

Didnt work. Heres my partitioning, if anyone can give me the proper input it'd be much appreciated.

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047a60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  82  Linux swap / Solaris
/dev/sda2             511        3121    20972857+  83  Linux
/dev/sda3            3122       22702   157284382+  83  Linux
/dev/sda4   *       22703       30401    61842217+   7  HPFS/NTFS
  
```

---

### Post by sancho panza on 2008-03-31
I think Super Grub Disk should help fix that too. Have you gone thru [the documentation here]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#introduction")?

---

### Post by uberlube on 2008-03-31
Thats another thing I was curious about. Will SGD add windows to my existing grub, or will it just overwrite grub and make my system just boot into win?

---

### Post by Iowan on 2008-03-31
Does SGD require followup with **sudo update-grub** - or does it update grub also?

---

### Post by sancho panza on 2008-03-31
If I remember correctly, SGD will fix all problems and u'll have a grub with windows and linux. But i'm not 100% sure. Try going thru the complete documentation. Else, try booting from the SGD. All the options on the SGD are well explained. So u'll know exactly what you are doing before u actually do it.

---

### Post by uberlube on 2008-03-31
Well, I have tryed everything SGD has to offer and I still cannot make windows appear in grub. I can use it to boot into both, but this isnt something I want to do all the time. Im just going reinstall my /root and grub with it. If that solves the issue then ill mark this thread as solved.

---

### Post by ibuclaw on 2008-03-31
I'll come back in a minute or two with a few edits with more details:
But for now, this is my Windows grub command line:

```

root  (hd0,0)
savedefault
makeactive
chainloader +1

```

If this solves it, hurrah!

[EDIT]
Grub Menu can be editted from this text file:
**/boot/grub/menu.lst**

This is what the bottom of my file looks like:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

[EDIT #2]
Also make sure that your "**boot.ini**" file (Found in "**C:\boot.ini**" or "**/media/sda1/boot.in**", whichever OS you are looking at) hasn't been wiped on your windows partition.
If that is the case, here is a generic one that you can work with:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

```
Change to your needs.

Regards
Iain

---

### Post by adrian15 on 2008-04-01
> **uberlube said:**
> Well, I have tryed everything SGD has to offer and I still cannot make windows appear in grub. I can use it to boot into both, but this isnt something I want to do all the time. Im just going reinstall my /root and grub with it. If that solves the issue then ill mark this thread as solved.

For those of you that SGD questions check [SGD FAQ]("http://www.supergrubdisk.org/wiki/SGDFaq").

What you need for booting your Windows is:
Super Grub Disk (With Help) -> Windows -> Windows (Advanced) -> Boot of Windows -> Select Windows partition (4th one).

Need code on your menu.lst
```

title win
rootnoverify (hd0,3)
chainloader +1
makeactive
boot

```

Hope you do not reinstall Ubuntu ;).

adrian15

---

