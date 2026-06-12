---
title: "Two grub questions"
date: 2007-11-29
forum: General Help
---

### Post by Casual Fan on 2007-11-29
I've looked I can't find direct answers to these questions, so here they are:

In a previous install of Gutsy, I was able to his ESC when Grub starts and then press "e" to edit the boot-up command and remove the "splash" from the command line, so I just got the scrolling text udring boot. Otherwise, I get a black screen and it take a long time. I can do that change now, but the change doesn't persist if I shut down or reboot. How do I edit grub to make that change persist? 

Also, there was a check box somewhere that allowed me to display the Ubuntu splash screen with the progress bar. That worked quite well and it didn't slow down the boot. Where is this check box? I thought it was under Sessions, but I didn't see it there.

Thanks

---

### Post by viking777 on 2007-11-29
Edit /boot/grub/menu.lst and where it says "splash=xxx" change it to "nosplash"

---

### Post by erfahren on 2007-11-29
you can edit GRUB's menu.lst file
```

gksudo gedit /boot/grub/menu.lst

```
(that's with a small "L")

you can change the end of the kernel line there, but it will go back to default when the kernel is upgraded. there's also the part that says:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

it can be changed there as well, and will make it permanent.

There's excellent information on GRUB here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It can be gotten to through here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by erfahren on 2007-11-29
oh, what you were saying about having a check box

the startupmanager package has that option. It's not installed b default. look for it in Synaptic.

---

### Post by Casual Fan on 2007-11-29
Thanks! Will try these solutions this PM.

---

### Post by Casual Fan on 2007-11-29
I edited my screen resolution in usplash.conf to my native resolution (1280 x 800 widescreen), and also selected "show text" and "show splash screen" in startupmanager.  I now get the progress bar on startup and shutdown.

Thanks!

---

