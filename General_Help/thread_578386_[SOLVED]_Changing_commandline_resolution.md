---
title: "[SOLVED] Changing commandline resolution"
date: 2007-10-17
forum: General Help
---

### Post by MOhz on 2007-10-17
Hey everybody,
I have a 17" monitor and on the GUI I have 1280x1024 running, but when I change to the CLI I think it is at 800x600 or some other really lousy resolution. I know how to manipulate the xorg.conf file, but how do I change the res on the CLI? I think 1024x768, but preferably 1280x1024 at 24bit would be good.

Thanks!

---

### Post by por100pre1 on 2007-10-17
If using Gutsy try this first:

```
gksu displayconfig-gtk
```

if that is not enough, then try [this]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by MOhz on 2007-10-17
Thanks for your reply, but my xserver is fine. I want a better resolution on the terminals. So when I press [Ctrl]+[Alt}+[Fx], I want the resolution to be 1280x1024x24.
I have some remembrance that one has to add vesa= and some hexacode in the boot loader.

---

### Post by por100pre1 on 2007-10-17
Oh, my bad! :(

Check if Startup Manager does the task:

```
sudo apt-get install startupmanager
```

---

### Post by MOhz on 2007-10-17
Hey,

thanks man! That must be the setting I have been looking for since ever! I cannot reboot my computer at the moment, but I am positive that it is right! Thank you thank you! I love the Linux community!

PS: I prefer aptitude... :lolflag:

---

### Post by por100pre1 on 2007-10-17
Check if it works fine after reboot, just to be sure. It is a good idea to create a rescue disk using the advanced settings. :)

---

### Post by olejorgen on 2007-10-17
This is only for gutsy? I can't find startupmanager in the repos.

---

### Post by por100pre1 on 2007-10-17
> **olejorgen said:**
> This is only for gutsy? I can't find startupmanager in the repos.

Only for Gutsy, it is good for changing USplash and adding images to GRUB.

---

