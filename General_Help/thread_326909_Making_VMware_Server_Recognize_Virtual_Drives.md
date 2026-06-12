---
title: "Making VMware Server Recognize Virtual Drives"
date: 2006-12-28
forum: General Help
---

### Post by smartbei on 2006-12-28
I just installed VMware according to [this]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server+howto").
I am now trying to install Fedora Core 6 in a VM, so that I can test it out without having to install it on a seperate partition. I downloaded the neccessary .iso files and mounted them to /media/VD1 and /media/VD2. How can I get the VMware server to recognize these as cdrom drives so that I can install FC?

Thanks.

---

### Post by raja on 2006-12-28
You dont have to mount the .iso in the host. In the Vmware server settings you can choose for the iso to be recognised as a CD drive. It will then be automatically be mounted inside the guest OS, allowing you to install from it.

---

