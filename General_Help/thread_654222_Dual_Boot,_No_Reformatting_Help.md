---
title: "Dual Boot, No Reformatting Help"
date: 2007-12-30
forum: General Help
---

### Post by ChestRockwell on 2007-12-30
Hello and Happy New Year everyone,
Sorry if this post is redundant, I did a search, but I didn't really see anything like this so decided to post a question.  

I have Ubuntu 7.10 running as my main OS on a 160GB single partition EIDE HDD.  I have another EIDE HDD with XP on it.  I would like to set up a dual boot but don't really know how.  I don't want to reformat any drives, both OS's are already installed I just need a way to choose which OS I start up.    Any way to do that?  Oh yea, just to be clear, the Ubuntu is my primary HDD and XP is the slave.  Any help would be greatly appreciated, even if its just a link to some other place.  Thanks in advance!

Joe

---

### Post by jken146 on 2007-12-30
If it's currently booting into Ubuntu, then all you need to do is add an entry for Windows in the file /boot/grub/menu.lst so that GRUB (the bootloader) gives you the choice.

Add the following to the end of that file.  ```
title		Microsoft Windows
root		(hdX,Y)
savedefault
makeactive
chainloader	+1
```

Where X is the hard disk number where Windows is (GRUB starts the numbering at 0, the equivalent of sda) and Y is the partition (again, starts at 0, the equivalent of sdX1).

---

### Post by alex1996arm on 2007-12-30
i had had this problem also,i have a quad boot.
but before i answer i need to ask a few questions
1.what operating system does it boot when it starts up?
2.are you sure that ubuntu is on the second hdd.


                        and happy holidays to you too:lolflag:

---

### Post by ChestRockwell on 2007-12-31
Well, I made the change to the menu.lst file, and that seemed to have worked, but...it just hangs on the the screen where it says 

starting up...

Here is the end of the menu.lst file and what II put into ite....
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=19143e52-82a0-4d5a-b85e-fc56d4860ae8 ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=19143e52-82a0-4d5a-b85e-fc56d4860ae8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Microsoft Windows XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

Also, HDD1, the windows drive is the slave, I know that and i know the drive is operational because it mounts fine in Ubuntu.

---

### Post by ChestRockwell on 2007-12-31
> **alex1996arm said:**
> i had had this problem also,i have a quad boot.
but before i answer i need to ask a few questions
1.what operating system does it boot when it starts up?
2.are you sure that ubuntu is on the second hdd.


1.  it boots into Ubuntu
2. Ubuntu is on the first HDD

---

### Post by alex1996arm on 2007-12-31
maybe it is just that you need to move the windows entry a line down?
it is like c++ but without a debugger!:lolflag:

---

