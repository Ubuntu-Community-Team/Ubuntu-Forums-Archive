---
title: "a temporary boot to console from grub"
date: 2013-05-11
forum: General Help
---

### Post by clearski on 2013-05-11
Hello!

I am trying to temporarily boot to console (shell prompt) directly from Grub. I know it's possible by modifying /etc/default/grub, but I only want to do this for a quick *temporary* session, without loading all the graphic stuff, so that at the next boot the GUI will load as usual.

I think it's possible, but I don't know how to do it.

Thank you!

---

### Post by matt_symes on 2013-05-11
Hi 

Boot into grub as normal. When you select you kernel press the e key to edit the kernel command line.

Navigate to the line that contains the word "quiet splash" and add the word "text" (no quotes) after it.

Press ctrl + x or F10 to continue booting.

Check your run level with the command ```
runlevel
```.

Check for

```
N 2
```

Hopefully you should be in a multi-user run level at that point. If not then please post back.

Kind regards

---

### Post by clearski on 2013-05-11
> **matt_symes said:**
> Hi 

Boot into grub as normal. When you select you kernel press the e key to edit the kernel command line.

Navigate to the line that contains the word "quiet splash" and add the word "text" (no quotes) after it.



I wasn't able to edit the kernel command line. When I boot into grub, I am presented a menu:

```
Ubuntu
Advanced options for Ubuntu
Memory test
...
```

I tried the first two menu entries and after I pressed **e** I read this:

```
setparams "Ubuntu"
    record fail
       load_video
       gfxmode ....
       insmode ...
```

There's not quiet option to follow, even though my grub config file in /etc/default contains:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```

I tried to add text to the parameters, but it's the same result, it goes into graphical. I think I have to figure out how I can edit the kernel loading options...

---

### Post by clearski on 2013-05-11
Sorry, it was just in front of my eyes, but I couldn't see it...

I found the kernel and the "quiet" option and everything works fine now with just adding "text".

Thank you!

---

