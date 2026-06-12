---
title: "How to Save Settings on a Live USB? Persistent"
date: 2015-04-07
forum: General Help
---

### Post by jasonfngp on 2015-04-07
I setup a live USB with pendrivelinux.com and selected a 1 GB persistence file to add to the USB stick. I booted into Ubuntu and setup wifi with a password, changed the desktop wallpaper and changed a bunch of settings.

The next time I booted into Ubuntu off the USB none of the changes were saved. I thought that was the point of the persistence file. What else do I need to do?

---

### Post by tea for one on 2015-04-07
Good evening

Pendrive Linux has a vast number of instructions/guides, which one did you use?

However, it may be quicker if you boot your live Ubuntu USB and use Start Up Disc Creator to install a persistent live Ubuntu on another USB device.

Start Up Disc Creator is already included in the standard Ubuntu distro.

I have found that this utility is reliable.

Kind regards

---

### Post by sudodus on 2015-04-07
I can add some links to help you get some more information about booting and persistence,

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[LiveCD/Persistence]("https://help.ubuntu.com/community/LiveCD/Persistence")

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

Good luck :-)

---

### Post by jasonfngp on 2015-04-08
I found the answer. All you need to do is add a user in the user accounts section. If you just use the standard guest login the changes will never save.

---

### Post by sudodus on 2015-04-08
That's right, user data and system data are saved in a persistent live system. But the guest user account is set up such that it will be wiped after logout, so so user data are saved. The default live user's data will also be saved, you need not add a new user.

---

