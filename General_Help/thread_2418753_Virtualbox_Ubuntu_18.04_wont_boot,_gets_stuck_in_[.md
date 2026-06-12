---
title: "Virtualbox Ubuntu 18.04 wont boot, gets stuck in [OK] Started GNOME Display Manager"
date: 2019-05-10
forum: General Help
---

### Post by miquel98 on 2019-05-10
After a sudden shutdown during an OpenFoam simulation my guest Ubuntu OS won't boot on Virtualbox 6.0.. Every time I try to initiate the virtual machine it gets stuck in the following command: "*[OK] Started GNOME Display Manager *". I have already tried to switch some VirtualBox parameters such as: number of CPU processors, RAM, deactivate 3d acceleration or graphic controller but it doesen't seem to help. Is there any way to solve this? Or there's at least a method to recover the files that were in guest Ubuntu 18.04 OS (64 bits)? My host OS is Windows 10 64 bits. Any suggestions will be welcome.

Thank you all!

---

### Post by SeijiSensei on 2019-05-11
You can create a clone of your virtual machine from the VirtualBox manager application. That will preserve all your files in case disaster strikes. Now boot the 18.04 VM into recovery mode. (Hold down Shift if the menu doesn't appear on its own.)  Then back up /home and any other directories you've customized separately to a location outside the virtual machine. 

One convenient location is another part of the host's filesystem outside the boundaries of the VM. With the Extension Pack installed, you can make a "[shared folder]("https://www.virtualbox.org/manual/ch04.html#sharedfolders")" on the host's file system available to the guest. 

I'd then install 18.04 again in a new virtual machine. Once it's running correctly you can copy over the files you saved using shared folders. Worst case, if you lose something you wanted to back up, you can start up the cloned copy of the old VM in recovery mode and copy off the files you need.

---

### Post by miquel98 on 2019-05-11
Thank you for answering! I've reached the panel of recovery mode after doing the cloning as you suggested, but I don't know how to back up/home from there. Could you explain me how to do so? I'm kind of new in Ubuntu and I'm not really familiar with those expressions and processes.

---

### Post by SeijiSensei on 2019-05-11
Did you set up a virtual folder through the VirtualBox manager?  

If not, you can try inserting a USB drive and see if the virtual machine sees it. You might have to play around a bit with the USB settings in the virtual machine definition.  Take a look at this: [https://www.smarthomebeginner.com/access-usb-drive-in-virtualbox-guest-os/](https://www.smarthomebeginner.com/access-usb-drive-in-virtualbox-guest-os/)

---

