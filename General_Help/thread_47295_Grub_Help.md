---
title: "Grub Help"
date: 2005-07-08
forum: General Help
---

### Post by computermann24 on 2005-07-08
Hey

This computer is all used by Family Members who are Windows Mad - However i like Linux! I am wandering under Ubuntu Hoary Headgehog how do you make Windows the Defualt Bootup? in Grub I have tried but this command line stuff is getting to me!

Thankyou

---

### Post by spd106 on 2005-07-08
Hi, you need to edit the /boot/grub/menu.lst file.

This can be done in gedit, but you will need to be root. So enter this from the cl
```
$sudo gedit /boot/grub/menu.lst
```

You need to count the title entries, starting at zero and only the uncommented ones. Then put the number of the one you want at the top.
ie 

*default 5*


```
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.10-5-386
boot

title           Ubuntu, kernel memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
```

This will boot into windows as default.

Now you will probably want to hide the menu from the windows users. So uncomment the hiddenmenu line. 

*hiddenmenu*

Then 

[I]timeout 5
[/I]
will give five seconds before loading the default choice.

After you've saved the changes run 
```
$sudo update-grub
```

If you have any trouble then please post this file and we'll take a look.

Hope this helps.

---

### Post by tonym on 2005-07-08
Only problem with this is that the number of entries in the automatically generated list may change when you next install a new kernel.

Move the Windows entry to the top of the list above the generated entries and leave default at zero ( or is it 1?).

---

