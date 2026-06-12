---
title: "[SOLVED] gnome-shell high CPU use - only uses software renderer"
date: 2014-04-03
forum: General Help
---

### Post by mathew4 on 2014-04-03
Ok so this is what I'm trying to figure out.

Right now I have Ubuntu 13.10 on an optimus laptap (HD4000 + GTX 670MX), nvidia-319 and nvidia-settings-319 installed, with a working bumblebee setup.
I also have Gnome 3.10 installed.

Now my problem is, Gnome Shell only wants to use the software renderer, which is using anywhere from 20-40% CPU. I've been searching all over Google trying to find the cause. A few solutions were to edit xorg.conf, which didn't help as I didn't have one where it should be (I know what the file is).

Is there anything I can do to force Gnome Shell (or any of the rendering) to use either my dedicated graphics, or integrated? If there is any info I need to post, just let me know.
(hopefully someone has the solution D:)

---

### Post by steeldriver on 2014-04-03
Hello and welcome to the forums

AFAIK there's nothing to stop you creating an /etc/X11/xorg.conf file - in fact, nvidia-settings should have an option to save the current settings ('X Server Display Configuration' --> 'Save to X Configuration File') which you can use as a base.

I don't know how to diagnose your particular issue - you could start by checking for any errors in the Xorg log file

```
grep '(EE)' /var/log/Xorg.0.log
```

You might want to change your thread title to something more specific, so that it catches the attention of folks with graphics troubleshooting experience

---

### Post by mathew4 on 2014-04-03
Yay, solved!

I just removed the Intel Open Source drivers, and reinstalled the default Ubuntu drivers.
Rebooted, and problem solved.

Note to self: Don't go near the Intel Open Source drivers...

---

