---
title: "boot menu ruined after attempt to customize with super boot manager"
date: 2015-08-22
forum: General Help
---

### Post by kira198520 on 2015-08-22
Hello.

I have Ubuntu 14.04.3 64-bits running a dual boot setup with Windows 7 on my laptop, and tried (attempted) to change the load screen theme and boot menu colors with super boot manager.

First I changed the load screen theme which I reverted to the original ubuntu one after disliking it. Somehow this changed the boot menu colors to monochromatic and messed up the characters (brazillian portuguese). So I figured I would try to change that in SBM's grub manager tab, unsuccessfully. Then I downloaded grub customizer which also didn't work. Finally I tried Boot-Repair, also unsuccessfully although it changed the boot menu language to english. [URL="http://paste.ubuntu.com/12156150"]http://paste.ubuntu.com/12156150
[/URL]
After that I re-ran grub customizer to revert the boot menu language to brazillian portuguese. Even though colors are set properly on /etc/grub.d/05_debian_theme and /etc/default/grub this seems to have no effect. I did try "sudo update-grub" with no results, in fact /boot/grub/grub.cfg is not modified by update-grub, the colors remain monochromatic and the characters are still messed up.

I'm at a loss here.

---

### Post by oldfred on 2015-08-22
I have not used either of your tools to edit grub.
You may want to totally start over by using Boot-Repairs advaced mode to totally uninstall & reinstall grub.

Or manually reinstall it to house clean out the various changes.
 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub

Then you can try this:
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Colors only edit
gksudo gedit  /lib/plymouth/themes/default.grub
sudo update-grub

You also seem to have a lot of kernels, I might houseclean out many old ones. I normally keep 2, current and one older one just in case.
I prefer to use synaptic and search on linux-image.
      
 #Current kernel:
uname -a

---

### Post by kira198520 on 2015-08-23
> **oldfred said:**
> You may want to totally start over by using Boot-Repairs advaced mode to totally uninstall & reinstall grub.

That did it. :D

> **oldfred said:**
> Then you can try this:
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
Colors only edit
gksudo gedit  /lib/plymouth/themes/default.grub
sudo update-grub

I'll look into it later.

> **oldfred said:**
>  You also seem to have a lot of kernels, I might houseclean out many old ones. I normally keep 2, current and one older one just in case.
I prefer to use synaptic and search on linux-image.
      
 #Current kernel:
uname -a

I removed most of them, and figured I would remove the unused themes as well.

All is fine now, thanks. ;)

---

