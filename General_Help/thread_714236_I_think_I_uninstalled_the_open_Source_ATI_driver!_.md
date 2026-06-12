---
title: "I think I uninstalled the open Source ATI driver! Help!"
date: 2008-03-03
forum: General Help
---

### Post by msiegel on 2008-03-03
Hi all,

I think I uninstalled the Open Source ATI driver!  Any ideas how to get it back?  Everything I find online talks about how to install the binary ATI drivers (non-open source).  Yes, the open source drivers come with Ubuntu, but what if I accidentally uninstall them?

Please help!

---

### Post by forestpixie on 2008-03-03
go to restricted drivers and re-enable it

if you reboot and it fails you might need to do this if it fails

dpkg-reconfigure -phigh xserver-xorg

how do you think you uninstalled it

---

### Post by Lunitik on 2008-03-03
Make sure xserver-xorg-driver-ati and/or -radeon is installed. You should just have 'xserver-xorg-driver-all' installed as per 'ubuntu-desktop'...

The previous person to reply, of course, is recommending you use the proprietary drivers...

---

