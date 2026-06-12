---
title: "UBUNTU Startup problem"
date: 2008-06-10
forum: General Help
---

### Post by sanjaymk on 2008-06-10
hello all,

when i start ubuntu, I end up in the terminal prompt prompting me for username/password, instead of taking me to the GUI username prompt.

The messages on the screen are 

usplash: setting mode 1152x864 failed
usplash: using mode 1024x718
kinit: name_to_dev_t
kinit: trying to resume from /dev/disk/by-uuid/....
kinit: No resume image, doing normal boot.

How do I fix it so that I can get to the normal GNOME? window or UI that will take me to the desktop.

Any replies are highly appreciated.  I am using Ubuntu version 7.10

Thanks,
Sanjay.

---

### Post by ubiqus on 2008-06-13
Same here. Anybody?

---

### Post by ubiqus on 2008-06-13
see [http://ubuntuforums.org/showthread.php?t=814933&highlight=kinit](http://ubuntuforums.org/showthread.php?t=814933&highlight=kinit)

---

### Post by spiderbatdad on 2008-06-13
Edit /etc/usplash.conf to 1024x768

X=1024
y=768
save & reboot.

---

### Post by ubiqus on 2008-06-14
> **spiderbatdad said:**
> Edit /etc/usplash.conf to 1024x768

X=1024
y=768
save & reboot.

This doesn't work...

---

### Post by sanjaymk on 2008-06-15
below is the solution that worked for me...

sudo apt-get install ubuntu-desktop
reboot

Courtesy: [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)


Hope this helps.

Sanjay.

---

