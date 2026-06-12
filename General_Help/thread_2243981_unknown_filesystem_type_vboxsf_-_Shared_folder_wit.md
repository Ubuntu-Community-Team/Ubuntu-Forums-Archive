---
title: "unknown filesystem type vboxsf - Shared folder with Virtual Box on windows"
date: 2014-09-12
forum: General Help
---

### Post by adrian38 on 2014-09-12
I've created a shared folder on Virtual box which is on C:\VirtualBoxShared on my windows 7 pc. I want to see this on my ubuntu 14.04.1 which is installed on virtual box.
I've installed guest additions using sudo apt-get install virtualbox-guest-additions.iso. This went through in about 3 minutes with no errors.
I've created the folder on linux in
/home/myname/VirtualBoxShared
I try and mount this with
sudo mount -t vboxsf VBoxFromScratch /home/myname/VirtualBoxShared
I get error message 'unknown fiilesystem type 'vboxsf''
Other help pages say to install guest additions (done) and change to 'vboxfs' but this gives the same error as well.

Other help posts in the archive just say to do what I've already tried.

thanks

---

### Post by TheFu on 2014-09-12
After installing the guest additions, the VM must be rebooted.
Are you certain the guest addition build was 100% successful? Did the driver kernel module actually get built and installed?

---

### Post by howefield on 2014-09-12
Try automounting the shared folder in the VMs settings and add your user to the vboxsf group in the Ubuntu guest, you should then find the shared folder in the Ubuntu /media folder.

---

### Post by adrian38 on 2014-09-15
Installed guest additions from VM (and not from linux cmd line).
Did the auto mount thing in VM. Dir now exists under /media
Added my user to vboxsf with sudo usermod -a -G vboxsf myname
Thanks howefield !

---

