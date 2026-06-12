---
title: "Boot Screen Not Showing"
date: 2008-05-13
forum: General Help
---

### Post by Patrick793 on 2008-05-13
I've been having this problem since Feisty. I'm currently using Hardy, on an actual Partition, unlike with Feisty. But anyway, how can I fix this.

I'm pretty sure the boot screen is showing, but I'm not sure. Everytime I boot Ubuntu, when the bootscreen should be showing, my monitor gives me a message saying "Input is Not Supported". It usually only does that with unsupported resoloutions.

This problem doesn't really affect anything, I'm just wondering how to make this go away (if possible).

My monitor is an Acer AL1706.

Thanks

---

### Post by strabes on 2008-05-13
Before I tell you how to do this, be aware that if you make a mistake in the file you edit you could be left with a (temporarily) unusable system. If you do screw up, see the GRUB link in my signature for information about reinstalling GRUB.

With that said, first edit your menu.lst file:[code]gksudo gedit /boot/grub/menu.lst[code]

Find the section towards the bottom which looks like this:> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=042b1b97-d508-4c2a-bc16-caf90ba5e142 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

Remove the word "splash" from the kernel line. **Do not** make any other changes. Save and close the file, and restart your computer.

---

### Post by KooW on 2008-12-29
Thanx strabes, this fixed my problem,  i have a old DELL server that did not show anything at boot
now i can see it all :)

---

### Post by Galban on 2009-05-09
Same monitor, same problem here. But It happens after changing the boot screen for the Bios. Because before that, it was working just perfect. I upgraded from 8.10 to 9.04 without problems. Once I decided to change the boot/background screen for the Bios, it went until the log-on screen, then I shot it down. Since then, after the Ubuntu's splash, I'm getting a blank screen with a message "input not supported", but I can ear the log-on sounds and even after entering user/password I can ear the Ubuntu's drums playing but in a blank screen. I Did a fresh install of 9.04 and no problems until I activate the restricted drivers for my Ati's HD4870 pci-E GPU, then again I got that "Input not supported message". I been trying many thing from the "safe mode" booting with the option to fix the X-server, even the Old method "dpkg-reconfigure xserver-xorg" is not applicable anymore to fix this. It is dual boot system and no issues on Vista.

So then lets see if somebody knows how to fix it!

---

