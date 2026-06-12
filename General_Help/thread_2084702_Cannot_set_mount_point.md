---
title: "Cannot set mount point"
date: 2012-11-16
forum: General Help
---

### Post by Mutinize on 2012-11-16
I'm fairly new to any distro of linux and I've had no serious errors until now. I've been running into a kernel panic and I'm trying to reinstall ubuntu from a liveusb but I cannot set my ubuntu partion's mount point to /. I've been searching google for quite a while but I've found nothing. Can someone please help?

I've been following the steps posted here : [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation).
I'm running Ubuntu 12.10 64x dual booted alongside Windows 7 Ultimate if that helps.

---

### Post by anaconda on 2012-11-16
> **Mutinize said:**
> I'm fairly new to any distro of linux and I've had no serious errors until now. I've been running into a kernel panic and I'm trying to reinstall ubuntu from a liveusb but I cannot set my ubuntu partion's mount point to /. I've been searching google for quite a while but I've found nothing. Can someone please help?

I've been following the steps posted here : [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation).
I'm running Ubuntu 12.10 64x dual booted alongside Windows 7 Ultimate if that helps.

I think you need to go to the edit partition, and from there select the mount point to be "/" 
You dont need to type it just select it from a dropdown menu.

---

### Post by Mutinize on 2012-11-16
> **anaconda said:**
> I think you need to go to the edit partition, and from there select the mount point to be "/" 
You dont need to type it just select it from a dropdown menu.Would I be editing it through gparted or the installation prompt? I cannot seem to edit it from either, though from what I've read gparted cannot set a mount point.

---

### Post by Mutinize on 2012-11-16
I've solved it, my bad. I had to set it to a ext4 partion to do it. Thanks for your help!

---

