---
title: "Ubuntu Dual Boot on Windows - GRUB2 Issues"
date: 2016-05-25
forum: General Help
---

### Post by devnull3 on 2016-05-25
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I have been using Ubuntu on a USB for sometime and decided to install alongside my current Windows 10 OS (Installed [/COLOR]Ubuntu 16.04 LTS)[COLOR=#000000]. I am relatively familiar with Linux systems, but in no way a professional. It was a smooth install and I had been using it for a month with no issues. Prior to installing Ubuntu, I had been partitioning sections of my drive for various reasons, so I am familiar with that. The other day I was cleaning up some unallocated space and I noticed a partition that didn't look familiar. Throwing caution to the wind, I deleted that partition and merged it with my C:\ (I believe it was ext4) which I suddenly realized with was for the Ubuntu OS. [/COLOR]

[COLOR=#000000]Now, when I turn my computer on, I get this message:

[/COLOR]GNU GRUB version 2.02~beta2-36ubuntu


Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.


grub>
[COLOR=#000000]
**I have been doing some research and most of the options I find do not work for me. I also find it odd that standard commands like 'history' don't work. It is also odd that if I insert a USB drive with a recovery image, my computer doesn't recognize the drive, nor can I try to list the drive in GRUB. Also, I'm not entirely sure but when running 'ls' it looks like my filesystem is incomplete or corrupt.

-Long story short, is there anything that I can do to either:
1. Get back to Windows OS or the Windows BIOS (I'd be fine with restoring my system -- I do not have a recovery disk or drive because normally I reset the system from Windows RE)?
2. Set the correct bootloader to repair or load into the Ubuntu menu to choose systems -- or chainload into the Windows OS from GRUB?
3. Completely remove all Ubuntu files from GRUB so I can load my Windows BIOS?

My system in GRUB shows:

grub> ls
(hd0) (hd0,gpt7)[/COLOR][COLOR=#000000](hd0,gpt6) [/COLOR][COLOR=#000000](hd0,gpt5) [/COLOR][COLOR=#000000](hd0,gpt4) [/COLOR][COLOR=#000000](hd0,gpt3) [/COLOR][COLOR=#000000](hd0,gpt2) [/COLOR][COLOR=#000000](hd0,gpt1)
[B]grub> ls (hd0,1)
(hd0,1): Filesystem is fat[/B].
[/COLOR][COLOR=#000000]grub> ls (hd0,2)
(hd0,2): Filesystem is unknown.
[/COLOR][COLOR=#000000]grub> ls (hd0,3)
[/COLOR][COLOR=#000000](hd0,3): Filesystem is unknown.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]grub> ls (hd0,4)
[/COLOR][COLOR=#000000](hd0,4): Filesystem is unknown.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]grub> ls (hd0,5)
[/COLOR][COLOR=#000000](hd0,5): Filesystem is unknown.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]grub> ls (hd0,6)
[/COLOR][COLOR=#000000](hd0,6): Filesystem is unknown.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]grub> ls (hd0,7)
[/COLOR][COLOR=#000000](hd0,7): Filesystem is unknown.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]grub> ls (hd0)
[/COLOR][COLOR=#000000](hd0): Filesystem is unknown.[/COLOR][COLOR=#000000]


Looking forward to a response. Thanks![/COLOR]

---

### Post by kansasnoob on 2016-05-25
Please post the url produced by running Boot Repair if possible:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You may need to press a key or key combo when booting your computer to display the BIOS/UEFI boot menu & get a live DVD/USB to boot.

---

### Post by devnull3 on 2016-05-25
Awesome, I was able to get into my BIOS! For some reason F2 never worked when I would boot just windows (assuming UEFI) but it worked this time and I'm back up and running.

Would you recommend running a boot repair in the currently installed Ubuntu or just restarting from scratch and install a new copy? 

Thanks again!

---

### Post by kansasnoob on 2016-05-25
Can you now boot both Windows and Ubuntu?

---

### Post by devnull3 on 2016-05-25
Negative. When trying to boot to Ubuntu, it takes me right back to Grub.

---

### Post by yancek on 2016-05-25
Probably the best thing to do is to run boot repair but do NOT try to make any changes.  Select the option to Create BootInfo Summary and post a link to that output here and someone should be able to suggest something.

---

### Post by oldfred on 2016-05-25
Post link to summary report from Boot-Repair as requested in post #2.

But if you deleted Linux partition, you probably need testdisk to see if you can find partition and restore it.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by devnull3 on 2016-05-25
Yep, looks like the Linux partition is gone. I'm going to run through Testdisk and take a look at UEFI boot install and repair. If that doesn't work, I'm going to reset this entire computer since it's a dev computer anyways.

Marking this thread as solved.

Thanks for the help...much appreciated!

---

