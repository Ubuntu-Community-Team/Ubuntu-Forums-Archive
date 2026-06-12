---
title: "[SOLVED] Worst display driver issue ever!"
date: 2008-01-27
forum: General Help
---

### Post by tranquito on 2008-01-27
Last night I ruined my own life. I was playing with the restricted drivers for my Nvidia Geforce 2 graphics card and I changed the drivers to a similar one in the hope that compiz effects would work. I then logged out so that the chandes would take effect.....

Black screen, then my moniter went to sleep.
In my brilliance I thought it would be a good idea to hard reboot my computer. This added even more fun to my situation. Linux did its standard checking disks for errors except for some reason it decided to find some:
/dev/hdd2  contains a file system with errors, check forced.
/dev/hdd2:
Duplicate or bad block in use!
 
/dev/hdd2: Multiply claimed bock(s) in inode 343694: 922917 922918 922919
                                                                       343730: 922917 922918 922919

Then it freaked out and said:
The automatic file system check of root failed. A manual fsck must be performed. The fsck should be performed root fs in read only mode.

I don't know anything about shell commands so I tried just typing fsck and it tried and failed.
I then pressed ctrl-alt-del to get out of shell and I got another error message when it tried to boot into my log in screen:
Could not start X server due to some internal error. Please restart GDM when corrected.

What should i do, i'm quite bothered by this?! I can access my file system through a Fedora live cd I happened to have lying around. Thanks in advance for any help.

---

### Post by taurus on 2008-01-27
Reboot it again and if you still get the same error message about manually run fsck, run

```
fsck -y /dev/hdd2
```

---

### Post by sumguy231 on 2008-01-27
Now would be a good time to use that LiveCD to get any important files to a safe distance. Then try running fsck from recovery mode. Press Esc when prompted to on bootup to get to the bootloader menu and select recovery mode.

---

### Post by tranquito on 2008-01-27
Thank you so much you saved my life, everything booted up normally after i did the fsck thing. But when the check finished, before i rebooted i got the:Could not start X server due to some internal error. Please restart GDM when corrected. Now that everything is ok should i be worried about this?

---

### Post by Raccoon1400 on 2008-01-27
type this in a console

dpkg-reconfigure xserver-xorg

 to reconfigure the xserver.

---

