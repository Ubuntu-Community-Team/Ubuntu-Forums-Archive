---
title: "[SOLVED] Old versions of Ubuntu in Boot Menu"
date: 2007-10-21
forum: General Help
---

### Post by f37u5g0d on 2007-10-21
How can I get rid of the old versions of ubuntu to stop showing up in my boot menu.  I now have a total of 7 os choices.  2 for the latest update of ubuntu (7.10) (normal and safe mode).  4 for when I orginially installed ubuntu and the immediate update it made (7.04).  And windows xp.  How can I get ride of the 4 old ubuntus?

---

### Post by Maestro23 on 2007-10-21
One way is to go into Synaptic and search for "Linux Header".  Should see all that you have installed.  Just uninstall the old ones.

---

### Post by manatee7 on 2007-10-21
i have the same problem, can i stop it from automatically adding more or should i just use my vista boot loader?

---

### Post by drs305 on 2007-10-21
1. Remove older versions, as Maestro23 suggests.

Edit /boot/grub/menu.lst  (using root privileges)

2. Uncomment any lines you don't want to see in the startup menu. This is a pretty crude method but works, especially if you might want to see the options later.

Example: (I didn't have any old kernels, so this is an example. If you are using Gutsy, DO NOT comment out Ubuntu 7.10)
```

# title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.22-14-generic # #root=UUID=d5ba3eda-1bce-4df5-a98f-9aba33e81104 ro single
#initrd		/boot/initrd.img-2.6.22-14-generic

```
You wouldn't see "Ubuntu 7.10, kernel 2.6.22-14 generic (recovery mode)" in your choices.
You haven't uninstalled this kernel and can re-edit menu.lst and uncomment the lines to see this option later if you choose.

3. There is a line in menu.lst 
```
# howmany=all
```

This line tells the menu list how many kernels to show as options. You can change this to an integer to tell menu.lst how many kernels to show on the menu. There are 2 interesting aspects to this. First, you change  'all' to a number but you LEAVE the comment symbol ( # ) in place. The instruction disregards the comment symbol for some reason and executes the instruction. Second, this change will only take effect when the next new kernel is installed. You won't see a change until the next kernel is released.  

```
# howmany=2
```

Note: manatee7, changing the 'all' to a number (2) would keep the list from growing any larger.

---

### Post by f37u5g0d on 2007-10-22
I tried uninstalling the older versions of ubuntu with synaptic but they still appear when I boot.  (they are gone from synaptic).  I want to try the method on the terminal mentioned in this thread but I am only familiar with java code and I only know the very basics.  In java a comment is " // " what is the symbol for a comment and how do you use them in the terminal?

---

### Post by drs305 on 2007-10-22
Edited: Read post #7 by geirha for the easiest way to shorten the number of visible entries during boot. Read below for remarks about using comment symbols to hide lines or enter remarks that won't be read or executed.

Concerning elimination of old kernels, the best method is to change the 'howmany' entry but here's the info you asked for about comments:.

The 'comment' symbol is a pound # symbol.
If you have deleted older kernels, you can erase the entries instead of commenting them out. I'd recommend you comment them unless you are sure you are deleting the correct entries.

First, make a backup copy of menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Then edit the menu.lst to do what I described earlier.
```
gksudo gedit /boot/grub/menu.lst
```


Here is part of my menu.lst:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ba3eda-1bce-4df5-a98f-9aba33e81104 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ba3eda-1bce-4df5-a98f-9aba33e81104 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

As an example, if I wanted to hide the memtest entry, I could change it to:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ba3eda-1bce-4df5-a98f-9aba33e81104 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5ba3eda-1bce-4df5-a98f-9aba33e81104 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,4)
#kernel		/boot/memtest86+.bin
#quiet

```

Later, I could go back and just delete the section that I commented out. This is only an example, I would not delete the memtest entry....

---

### Post by geirha on 2007-10-22
You only need to change that one line to limit the number of ubuntu kernels showing up on the boot menu. (the "# howmany=all" to "# howmany=2". Then run ```
sudo update-grub
``` and it will remove all but the two newest ubuntu entries.

---

### Post by drs305 on 2007-10-22
> **geirha said:**
> You only need to change that one line to limit the number of ubuntu kernels showing up on the boot menu. (the "# howmany=all" to "# howmany=2". Then run ```
sudo update-grub
``` and it will remove all but the two newest ubuntu entries.

Even easier! I didn't know that command would update 'howmany' before the next kernel was downloaded.

---

### Post by f37u5g0d on 2007-10-23
Thanks so much for all your help drs 305.  Problem solved!

---

