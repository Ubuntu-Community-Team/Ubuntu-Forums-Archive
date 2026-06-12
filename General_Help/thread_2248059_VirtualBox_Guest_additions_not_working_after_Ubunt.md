---
title: "VirtualBox Guest additions not working after Ubuntu 14.04 update"
date: 2014-10-12
forum: General Help
---

### Post by Nick_Lambert on 2014-10-12
I have Ubuntu running in Oracle VirtualBox on a Windows 8 laptop. I have just installed the latest Ubuntu updates and now Ubuntu runs in small window on the screen. Guest Additions is supposed to adjust the window size to full screen but for some reason it is not working anymore. Any ideas how I can fix this? Or is this a question for VirtualBox?

Thanks

---

### Post by westie457 on 2014-10-12
Welcome to the Forum Nick_Lambert

Have you tried to install (or reinstall) the Guest Additions to the Guest machine and then logging out and back in? This usually works for me.

---

### Post by Nick_Lambert on 2014-10-12
I tried reinstalling GA but I get an error message saying that it is locked. It may be that I am reinstalling incorrectly - I'm new to both VirtualBox and Ubuntu.

---

### Post by ajgreeny on 2014-10-12
Try installing the GA into VB without a guest OS running; when I started VB in my Xubuntu 12.04 host, after it was updated, it automatically told me that I need to update the guest additions and offered to download and install them.  Then after starting a guest Ubuntu 14.04 OS I installed the new version of GA in my Linux guests by first opening a terminal and going to root with command ```
sudo -i
``` Then I opened the VBOXADDITIONS_4.3.18_96516/ from Places in the file manager of the guest OS and ran the **VBoxLinuxadditions.run** file in that terminal by simply dragging it across from nautilus to the root terminal.  As the terminal is root you do not need to run the script with sudo.

That should solve it for you as well.  Any difficulties, come back again and ask.

---

### Post by ibjsb4 on 2014-10-12
It is also necessary to have 'virtualbox-guest-dkms' installed in the ubuntu guest when upgrading.
```
sudo apt-get install virtualbox-guest-dkms
```

---

### Post by Nick_Lambert on 2014-10-12
Thanks for your suggestions - I tried them, but without success. However, I appear to have resolved the problem now but am not really sure why. What I did was to clone the Ubuntu guest in the Virtualbox, figuring that it was better to experiment with a clone than to completely screw up the original. I then deleted the VboxGuestAdditions.iso file from the clone's Storage settings and started the clone. The clone opened using the full screen and I haven't discovered any collateral damage from deleting the .iso file yet. What I find most strange, however, is that when I then opened the original Ubuntu guest, it also opened with the full screen, even though it still has the.iso file in the Storage settings.

For the time being, I'm a happy bunny again.

---

