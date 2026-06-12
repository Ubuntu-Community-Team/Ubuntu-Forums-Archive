---
title: "GRUB Help"
date: 2007-04-29
forum: General Help
---

### Post by Ajjw on 2007-04-29
How do you configure GRUB to set Windows Vista as the primary OS? I want to put it at the top above Ubuntu as Windows is my most used OS.

Thank you.

---

### Post by davidgarcin on 2007-04-29
You have to modify /boot/grub/menu.lst.  To do this, at a command line type
```
sudo gedit /boot/grub/menu.lst
```

Your menu.lst should look something like this at the bottom:
```


title           Windows Vista
rootnoverify    (hd0,0)
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=4584a97e-4b52-403a-a1d0-510e2b44af35 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386


title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=4584a97e-4b52-403a-a1d0-510e2b44af35 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin

```

Except that for your Windows Vista entry, you have to put the correct partition in instead of (hd0,0).  The first number stands for the hard disk, the second number is the partition number.  So in my case, Vista is installed on the first hard disk on the first partition.

Note that there is also a "default" option you can set in the file that will automatically boot a menu option after a period of time specified by the "timeout" option.   It's fairly close to the top.  If you have Vista as the first entry (as shown above), the line should read:
```
default 1
```

Let me know if you have any problems, I struggled though this a while ago, so I'm glad to help.

---

### Post by jimbob on 2007-04-29
I believe that GRUB starts counting from 0 so if Vista is the first one in the list you would want to put in:    default   0
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by davidgarcin on 2007-04-29
good point... I was basing that off my menu.lst, but I forgot that it was counting a separator as a menu entry.

---

### Post by Ajjw on 2007-04-29
Thank you, it worked.

---

