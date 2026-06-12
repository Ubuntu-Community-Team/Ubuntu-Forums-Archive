---
title: "Grub - boot windows by default"
date: 2007-06-02
forum: General Help
---

### Post by BobSock on 2007-06-02
Can someone tell me what I need to change to make grub boot Windows XP Professional by default? 

I would also like to remove some of the boot choices, I'm guessing that I can just delete the entire section of code of the options I don't want there and they will be removed... (grub was just updated with newer installation of ubuntu so two versions are showing up.

```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6913ee83-3cc9-4410-bed5-277fbf47abeb ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=6913ee83-3cc9-4410-bed5-277fbf47abeb ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6913ee83-3cc9-4410-bed5-277fbf47abeb ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6913ee83-3cc9-4410-bed5-277fbf47abeb ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

---

### Post by jimbob on 2007-06-02
Edit the default parameter in /boot/grub/menu.lst to the   number -1 of the line shown on your grub menu (grub starts counting from 0).   So if XP is the sixth line on the menu, change the default line to [COLOR="Red"]default   5[/COLOR].

When deleting entries delete everything from the 'title' line down to the next 'title' line in the uncommented section at the bottom.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by BobSock on 2007-06-03
Thanks for the reply. It took me a little while to figure out what and where the default line was but I did find it and changed it. ;) GRUB is now edited and working great.

---

### Post by bishop9226 on 2007-06-03
why bother with that when someone made you a nice gui to change all your settings via system -> admin

[http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

---

