---
title: "Xserver broken how to reconfigure"
date: 2019-03-27
forum: General Help
---

### Post by DrScum on 2019-03-27
Ubuntu 18.04.2
Was dealing with the lost wifi icon problem, followed [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1774957](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1774957) #23
After installing the two .deb files the boot system dropped me to a terminal login, upon entering startx Xserver wouldn't start anymore.
Trying to boot into recovery mode didn't help. With upcoming panic I did many stupid things one of which was installing lightdm. I am stuck with a lightdm login screen which tells me upon entering the password "failed to start session", which is not surprising knowing that Xserver doesn't start.
I did already boot from CD with puppy linux and have a solid backup of my data. However, reinstalling from scratch and getting the system tweaked to where I was still would take a lot of time. Thus I would still prefer a fixing option.

How can I get back to a terminal login? How can I possibly reconfigure Xserver?

Thanks for considering this.

---

### Post by TheFu on 2019-03-27
If the system boots, ask for a different tty - press <cntl>-<alt>F1 through F8 to change ttys.
Or you can boot from a live-boot flash/optical disk with the same Ubuntu release and go into recovery mode, setup a chroot for the HDD directories and modify things to your desire.

Also, what are the errors in the Xorg.0.log file?

And after you get all this fixed, perhaps having a backup and restore process that will get you back to the same system, same settings, same configs, same data in 30-45 minutes is needed?  It isn't THAT hard to make a backup script to handle versioned backups for all the important stuff, settings, data, and list of manually installed packages. With that data, you can have YOUR setup back in the timeframe above.

---

### Post by DrScum on 2019-03-27
Thank you for your reply.

Firstly, I do daily backups using Grsync, but that covers only data, not the system. If you could point me to some literature on how to learn to set up a backup system the way you describe it that would be very much appreciated.

Secondly: the Xorg.0.log file can be found here: [https://drive.google.com/file/d/1ubzQ0xV1xiMGaMlrqBQ1lvdjQGkMEMv_/view?usp=sharing](https://drive.google.com/file/d/1ubzQ0xV1xiMGaMlrqBQ1lvdjQGkMEMv_/view?usp=sharing)

---

### Post by DrScum on 2019-04-05
Tried to follow The Fu's instructions:
"If the system boots, ask for a different tty - press <cntl>-<alt>F1 through F8 to change ttys", however, the system doesn't respond to the key combination. Thus I am stuck with the lightdm login page (see initial post)

I also did try to boot from the install DVD but wasn't able to "go into recovery mode, setup a chroot for the HDD directories and modify things to your desire". Where could I look up on how to do that? What would I have to modify in order to get the xserver back?
btw. I did post the Xorg.0.log file above.

---

