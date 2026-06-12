---
title: "Where are Removable Drives and Media settings stored?"
date: 2007-08-19
forum: General Help
---

### Post by Johbuntu on 2007-08-19
I get an fsck error when booting in both recovery and normal mode. I'm sure that this has something to do with the USB flash drive i've been using to shuffle data around with. The flash drive started appearing (icon) twice on the desktop, probably from unplugging it once without unmounting it - I don't remember exactly.

My fstab is fine - so says all the reading I've been doing.

If I boot off the LiveCD I know that I'm not going to fix anything by playing with the Removable Drives and Media system preferences control panel, because it wont save to my actual filesystem. Also, from the live CD I can tell that my hard disk partitions are all just fine.

My question is: Where are such settings stored - file/directory - the settings that my system tries to boot with re: automount devices.

Though, I might be barking up the wrong tree?

Please and Thank you!
--
Joh.

---

### Post by ajgreeny on 2007-08-19
Can you boot with the removable usb drive removed?  If so, do it and then see what happens when you plug in the usb drive again.  If all is OK, make sure all your files are off the drive and then reformat it.

---

### Post by jnorthr on 2007-08-19
no don't think you are barking wrong, my machine does similar with an external  usb 20Gb freecom hard disk. If i fail to unmount it , ubuntu complains and will not 'see' it again unless i reboot. If it does perchance 'see' it there is no desktop icon but i can look in /media folder for the mount point and click there to gain access. There is a feature called udev which examines the hardware at boot time and creates an entry (or several) depending on what it finds. I believe (but cannot confirm) that hot plugable devices like usb thumbs,etc are not treated in the same way. It's a fascinating topic which i'm just starting to look at.

---

### Post by Johbuntu on 2007-08-20
thanx for the replies people. Still no solution, though the problem has morphed somewhat, as reflected in the question I posted up at [https://answers.launchpad.net/ubuntu/+question/11792](https://answers.launchpad.net/ubuntu/+question/11792)

---

