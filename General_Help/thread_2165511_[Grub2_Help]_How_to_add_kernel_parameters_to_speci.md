---
title: "?[Grub2 Help] How to add kernel parameters to specific menu items?"
date: 2013-08-05
forum: General Help
---

### Post by KillerKelvUK on 2013-08-05
I've had to add a line in /etc/default/grub which reads "GRUB_CMDLINE_LINUX="mtrr_gran_size=2G mtrr_chunk_size=2GB" to resolve a kernel warning report for a straight forward Ubunutu 12.04.2 install.  This works fine and I have no issues with it.

I install Xen and the above line remains in place and Grub does its job of appending it to the Xen boot parameters, Xen doesn't like this and throws a kernel warning once booted.

How do I add the mtrr parameters only for my Ubuntu (without Xen) lines in Grub?

Thanks,

K

---

### Post by oldfred on 2013-08-05
I might add whatever boot stanza you need to 40_custom and maybe even turn off os-prober. I have so many installs I have to turn it off and only put the few working installs in 40_custom.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If that works, then turn off os-prober

 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

You can also copy boot stanza to a text file to make a custom menu and use grub2's config file to boot from that file.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I use config file entry to boot my ISO with loopmount from another partition on another drive. Then I only have to edit the text file with a new ISO or name change without having to run sudo update-grub. I always forget to run that after editing 40_custom.

---

