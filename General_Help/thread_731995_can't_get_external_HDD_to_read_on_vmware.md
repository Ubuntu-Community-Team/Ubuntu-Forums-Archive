---
title: "can't get external HDD to read on vmware???"
date: 2008-03-22
forum: General Help
---

### Post by chas85 on 2008-03-22
for some reason when i run vista ultimate in vmware (ubuntu gutsy) the external HDD won't read. normally i would not care but i can't get my driver i downloaded to work. i chose not to install vmware tools because it does not have support for fullscreen for my graphics card (i need 1280 x 800, not selectable with vmware tools for fullscreen). i was just going to download all the drivers manually and install them so i could do fullscreen and have all the feautures vista does normally. can anyone help with this or does anyone have any ideas? many thanks in advance.

---

### Post by warp99 on 2008-03-24
You could enable network shares then access the drive through the mount point, which would be listed in /media when the drive is attached. You could also edit the CD-Rom settings to access the drive as a "Virtual Device Node" through the /dev mount point.  

As far as the resolution that's a vmware issue. I would check the  online help files or the vmware forums for the answer. :)

---

