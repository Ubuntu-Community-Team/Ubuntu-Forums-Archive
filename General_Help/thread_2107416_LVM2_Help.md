---
title: "LVM2 Help"
date: 2013-01-21
forum: General Help
---

### Post by btallas on 2013-01-21
I've just installed Ubuntu 12.04_1 on my laptop using lvm2 for my root filesystem.  I made a /boot (ext4) and /swap partition separate from the logical volume root.  I've installed vmware player on the laptop (work laptop so installing windows 7 in vmware for work).  I'm creating a separate logical volume just for vmware (/home/my_username/vmware).  I've successfully created the logical volume and added the relevant entry in /etc/fstab.  My issue is every time I reboot, /home/my_username/vmware is mounted like an external disk and shows up like so on the unity side bar.  When opening the home folder it shows up as a 81gb file system up top.  Is there any way to prevent this from showing like so?  I just want it to mount like a standard filesystem, not like an external disk.

---

### Post by btallas on 2013-01-23
Bump...  Anyone else experience this?  Is my question too vague?

---

### Post by btallas on 2013-01-23
Found the answer myself.  In case anyone else ever has this issue, the solution is to install CompizConfig Settings Manager (sudo apt-get install compizconfig-settings-manager).  Open CompizConfig Settings Manager, click on Ubuntu Unity Plugin, then click the "Experimental" tab and under "Show devices" you can select to only show mounted drives or never show them on the Unity launcher.

Credit for this solution goes to [http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html](http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html)

---

