---
title: "Login screen won't come up"
date: 2008-04-28
forum: General Help
---

### Post by grkvenom23 on 2008-04-28
I restarted my computer with Ubuntu(gutsy) the other day and for some  reason the ubuntu screen comes up with the progress bar and after progressing to little spots the screen goes black and a blinking cursor is at the top left but i can't type anything i am a newbie to ubuntu i only had it on my computer for 2 weeks so if anyone can help i would really appreciate it.  Also i pushed Ctrl+Alt+F1 at the black screen and got this message:

Starting up...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/7705a972-53a9-4c9f-a652-cede8eb27af4) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/7705a972-53a9-4c9f-a652-cede8eb27af4
kinit: no resume image, doing normal boot...

and that's it, after this screen i tried typing in this:

sudo dkpg-reconfigure xserver-xorg

but i get nothing it just goes to a blank line where i can type in anything but no command gets processed.  Please i'm going crazy if anyone can help, please do.

---

### Post by TeoBigusGeekus on 2008-04-28
Boot into recovery mode with grub and type
```
sudo dkpg-reconfigure xserver-xorg
```
to do a readjustment of your graphical settings.

---

### Post by grkvenom23 on 2008-04-28
do i need to push e at recovery mode because when pushed enter at recovery mode i typed in what you told me and pushed enter but nothing happened

---

### Post by TeoBigusGeekus on 2008-04-28
Ok, type 

```
reboot
```

to reboot :)

reenter recovery mode and try

```
sudo dkpg-reconfigure -phigh xserver-xorg
```

---

### Post by grkvenom23 on 2008-04-29
still can't type anything in recovery mode i enter grub, select recovery mode, a whole bunch of code is processed and then i can type something in there but no command gets carried out, if anyone is reading this please give me any suggestion you have.  Also the light on the computer that flashes when its working, doesn't flash so i don't know if maybe thats got something to do with it and if it is a hardrive problem.

---

### Post by grkvenom23 on 2008-04-30
Anyone have any idea?  Please help

---

