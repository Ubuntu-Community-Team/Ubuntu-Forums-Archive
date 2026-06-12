---
title: "No splash screen, can I reinstall it?"
date: 2008-02-19
forum: General Help
---

### Post by gohanssjn on 2008-02-19
The first splash screen, after GRUB, but before the login manager, has gone missing.

How can I reinstall it?

I tried everything in this topic to no avail:

[http://ubuntuforums.org/showthread.php?t=694221&highlight=change+splash](http://ubuntuforums.org/showthread.php?t=694221&highlight=change+splash)

---

### Post by y-lee on 2008-02-19
hmmm

Check your grub **menu.lst** found in **/boot/grub**
 

Look for the part that looks something like


```
title		Ubuntu, kernel 2.6.15-51-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-686
savedefault
boot
```

on the kernel line does it have the splash option?

If not you need to edit that line and add splash. Save the file and test it. Be sure you make a backup copy. to edit

```
sudo gedit /boot/grub/menu.lst
```

Hope this helps, let us know :)

---

### Post by astrotech226 on 2008-02-19
Don't forget to add the splash option to the defoptions line, or the next kernel update will revert back to the old method.  In the menu.lst file, look for a line like this:
```

# defoptions=quiet splash
```

The script that generates the actual "kernel" line that is used at boot time is "update-grub".

---

### Post by gohanssjn on 2008-02-20
Splash is already part of the line.

---

### Post by y-lee on 2008-02-20
ok, it may be you need to set vga boot option in the menu.lst file. [See Bug #27837 in usplash (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/27837") and [BootOptions]("https://help.ubuntu.com/community/BootOptions#head-07d4b7411f7da70e337287db9a86ea941038b8b3")

> This list is not comprehensive but it contains some of the common options. When presented with the text on the screen "boot:" then the options below can be given. They must have the kernel name before the option.

Example: Adding the vga=771 option

boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash

boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash vga=771 

I'm not sure what to set vga to tho :(  

> 773 DID work! VGA=791 also works, and also 788 

Probably depends upon your video card

The code below will tell you more about your card.
```
lspci | grep VGA
```

---

