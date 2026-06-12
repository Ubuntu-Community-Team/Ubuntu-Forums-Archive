---
title: "Cannot log in after update to ubuntu mate 16.04"
date: 2016-07-12
forum: General Help
---

### Post by danbuz on 2016-07-12
Hi there guys,

After a dist-upgrade to the system I get this error on login 

```
 GLib-GIO-CRITICAL: g_settings_schema_source_lookup: assertion 'source != NULL' failed
mate-session[2168]: GLib-GIO-ERROR: No GSettings schemas are installed on the system
```

A dialog window said that I might run out of free space while installing. 
I tried to free up some space with live usb, but no success.

Any ideas? Thanks in advance!

---

### Post by danbuz on 2016-07-13
guys, anyone please?!

---

### Post by Impavidus on 2016-07-13
We've very little information to go on.

Can you get to a terminal and run these three command?```
df -h
dpkg --list | grep -v "^ii \|^rc "
dpkg --list linux-image\* linux-headers\*
```The first will tell disk space usage, the second should report any broken packages, the third will list the old kernel images and headers, which are a common cause of full partitions.

If you can't login to the graphical interface, try ctrl-alt-F1 from the login screen and login to the console. Use ctrl-alt-F7 to get back. Or use recovery mode and drop to a root shell.

---

### Post by danbuz on 2016-07-16
Thanks for the reply.

I could not able to connect to the network. I got this message:

[IMG]https://s32.postimg.org/w3e23whed/IMG_20160713_150107.jpg[/IMG]

The other two outputs are those. I'm sorry I'm not aware how to get text output, so I captured it:

[IMG]https://s31.postimg.org/elv90c9aj/IMG_20160713_150230.jpg[/IMG]

[IMG]https://s32.postimg.org/d6ulejlkl/IMG_20160713_150142.jpg[/IMG]

---

### Post by danbuz on 2016-07-19
Any suggestion guys? I'm still banging my head against the wall..

---

### Post by danbuz on 2016-07-20
Still no success, I need some advice. Please give me a hint..

---

### Post by webforumthread on 2016-08-04
I just did a update to 17.3 and now cannot boot. Same 'your session only lasted less than 10 seconds.'

mate schema null failed and 
no gsettings schemas are installed.
aborting...

Seeing how there seems to be no solution online yet, I guess its time to install a new HDD and install fresh.

That's what I hate about Linux. Just as bad as windows at times. I write this on my old Windows PC. Still going strong.

---

### Post by vasa1 on 2016-08-04
> **webforumthread said:**
> I just did a update to 17.3 ...
17.3?

This thread is about Ubuntu Mate 16.04. If you want to comment on Mint, their forum is here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

Or you could drop in here: [https://ubuntuforums.org/forumdisplay.php?f=453](https://ubuntuforums.org/forumdisplay.php?f=453)

---

