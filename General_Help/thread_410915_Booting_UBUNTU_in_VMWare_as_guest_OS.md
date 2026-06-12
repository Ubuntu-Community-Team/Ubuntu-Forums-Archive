---
title: "Booting UBUNTU in VMWare as guest OS"
date: 2007-04-16
forum: General Help
---

### Post by battleseals on 2007-04-16
Hello!

I have Ubuntu 6.06 installed on the separate partition on the single hdd with the WinXP.
Ubuntu works fine.
But.
 when I tried : WindowsXP+VMWare workstation 6 -> in which I try to start existing Ubuntu installation, it drop to console right after boot started and showed error like "can not mount /dev/sda3 as root file system" 

How to fix it? 

Any ideas appreciated.

Thanks!

---

### Post by Tanoku on 2007-04-16
This is more of a VMWare/Windows problem than an Ubuntu one, to be honest.

If your computer boots Ubuntu fine, then that means that you are doing something wrong with VMWare. I'm no guru on Virtual Machine sofware, but probably booting the Workstation with a Virtual Machine Image (*.vmx) instead of booting from a real partition may give more reliable results.

---

### Post by battleseals on 2007-04-16
Thanks,
but reinstall ubuntu on the virtual disk is not an option for me, unfortunately.

It looks more like Ubuntu kernel could not load appropriate SCSI module for vmware virtual scsi adapter. or same.

---

### Post by battleseals on 2007-04-16
Guys, any other ideas?

---

