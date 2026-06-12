---
title: "is &quot;startx&quot; equivalent to when i was &quot;not seeing&quot; Grub? =&gt; Sound and Scanner problems"
date: 2013-01-17
forum: General Help
---

### Post by mascip on 2013-01-17
Hello, in /etc/default/grub i changed this line :
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```into
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```so that now i login on the command line, and i have to type
```
startx
``` to start my desktop environment.
AS my ~/.xinitrc file was empty, nothing happened when i did startx. So i had to add ```
exec startlubuntu
```in this file. 
I wonder how my desktop environment was started before that: apparently not with startx, as the ~/.xinitrc file was empty. Is that right?

Since i have done this change in /etc/default/grub, my scanner is not recognized anymore by
Simple Scan (i can only find it if i use root permission with sane-find-scanner), and the sound doesn't work anymore. 

So, what is the difference between what happened before i changed /etc/default/grub, and now?

---

### Post by mascip on 2013-01-17
I think i found something. 
I think that before i changed grub, the system was using /etc/X11/xinit/xinitrc. For some reason, after i changed grub, startx doesn't seem to find this file anymore. 

In this /etc/X11/xinit/xinitrc there is only one line:
```

. /etc/X11/Xsession

```So, i thought that changing my ~/.xinitrc file to exactly the same thing would fix everything... but it didn't.
It could be because i did some changes to my initialization, like creating a custom udev-related file for the scanner to be found, and like starting a ACPI dameon (that was just to get rid of a warning, so i could undo it).

I have to leave work now, i'll keep on investigating tomorrow. 

Any insight or ideas will be very welcome :)

---

