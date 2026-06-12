---
title: "kernel panic??"
date: 2007-11-06
forum: General Help
---

### Post by lattmau on 2007-11-06
I installed gnome-splashscreen-manager and I activated a splash screen.  Then I tried rebooting to see if splash screen had changed.  

Except after the GRUB menu,  I get this message

> [18.279936] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Once it shows that message, its stuck there.  I don't know what this means.  I'm new to Linux and I just spent a lot of time customizing things.  

Does this mean I need to do a clean install?  Is there a fix?  Talk to me like I don't know anything.

---

### Post by mouseboyx on 2007-11-06
Clean install is the easiest

2nd option:
Boot the live cd of gusty 7.10 and then edit the file in /boot/grub/menu.lst
In terminal write:

If you know how to mount the drive skip this step:
```

fdisk -l
```find the name of your harddrive partition with ubuntu on it then insert it into where *device name* is
```
mkdir /media/harddrive
sudo mount /dev/*device name* /media/harddrive
``````
gksu gedit /media/harddrive/grub/menu.lst
```change it so that something similar to this

```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bb84a4b6-3290-43db-ae71-02c2de3b63b3 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet
```looks like this:

```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=bb84a4b6-3290-43db-ae71-02c2de3b63b3 ro quiet
initrd        /boot/initrd.img-2.6.22-14-generic
quiet
```make it so that the line
```

 root=UUID=bb84a4b6-3290-43db-ae71-02c2de3b63b3 [COLOR=Red]ro quiet[/COLOR]

```does not have anything after [COLOR=Red]ro quiet
[B]
[COLOR=Black]then see if it works!


[/COLOR][/B][COLOR=Black]```
[/COLOR][/COLOR] 			 				[18.279936] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

could mean that there is something wrong with the root (0,0) or something wrong with the file system

you could try editing it so that the root is (0,1) , (0,2) ...

---

### Post by lattmau on 2007-11-06
i got to this step :

> gksu gedit /media/harddrive/grub/menu.lst


and gedit showed that it was blank.  I listed the contents of /media/harddrive and i dont see a grub folder

---

### Post by mouseboyx on 2007-11-06
[CENTER]did you mount the drive with ubuntu on it
sudo mount /dev/xxx /media/harddrive

There is probably someone that can help you better than me but this way seems like it will work.

[/CENTER]

---

### Post by lattmau on 2007-11-07
i found the file in /media/harddrive/boot/grub/menu.lst and applied the edits you suggested, but still the same message.

am i missing something?

---

### Post by mouseboyx on 2007-11-07
[LEFT]this is not a sure fix I was just suggesting stuff sorry.  the custom splash messes with the kernel and rebuilds it.  I usualy just dont use a splash because i like to know whats going on.  Sorry about the bad expirience but with the ammount of times i have broken my instalation you shouldent be worried. (on accident and sortof on purpose.)
[/LEFT]

---

### Post by lattmau on 2007-11-07
thanks for the help though.

anyone else have an idea that doesn't require doing a clean install?

---

### Post by infra_red_dude on 2007-11-07
Most prolly the kernel image is messed up as he said above. I dunno if there is an easier method that exists, but this is the method I used when the kernel was messed up on my lappy:

1) Boot from the Live CD.
2) Mount your existing root partition (as you did above), ensure that its the correct partition.
3) Now ensure that the above mentioned lines exist in <mounted root partition>/boot/grub/menu.lst
4) Rename all the existing file in the folder <mounted root partition>/boot to something else (like adding .bak or .old at the end.) Make sure you rename all the files.
5) Now copy all the files from /boot to <mounted root partition>/boot. The /boot folder is the Live CD's boot folder.
6) Rename <mounted root partition>/boot/vmlinuz-<live cd version> to <mounted root partition>/boot/vmlinuz-2.6.22-14-generic
7) Rename <mounted root partition>/boot/initrd.img-<live cd version> to <mounted root partition>/boot/initrd.img-2.6.22-14-generic
8) Reboot your computer.

This has worked for me in the worst of the worst situations. Thats the reason I stick to gtweakui.

---

### Post by lattmau on 2007-11-07
i will try once i get home.

thanks! i'm really hoping this works haha

---

