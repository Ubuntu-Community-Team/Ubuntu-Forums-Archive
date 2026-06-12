---
title: "how to move my /boot to another hard drive"
date: 2008-03-16
forum: General Help
---

### Post by speed145a on 2008-03-16
i currently have /boot on a separate hard drive and i would like to move it to the same disk as everything else because the /boot drive is failing.

i was hoping to get some help figuring out what would be involved in this process.

1) is GRUB going to need to be reinstalled?

2) how do i make the changes needed to fstab?

3) are there any other configs that will be looking for the /boot that i need to change to point to the new directory on / ?


any other comments/thoughts on getting this done would be appreciated.

---

### Post by LeoSolaris on 2008-03-16
Well, now bear in mind that I am still new to Linux, but I am not new to computers in the slightest. 

If it is only /bbot, and nothing else, it sounds like a good time to use Gparted on the drive you want to keep, make a space big enough for the /boot and transfer everything over with a copy/paste. You will have to install grub to the hard drive's MBR, which you can do with Ultimate Boot CD (tool I found of distro watch) You will likely have to still edit a good bit.

I have never actually done what your talking about, so take the advice for what it's worth. It logicly should work. Ultimate boot CD is an excellent tool.

Make bloody well sure to back everything up! 

If you have a third hard drive, just doing a ghost to it of the /boot's hard drive should work, too. That might be the easiest solution.

Another solution would be to do a back up of everything on CD's or DVDs that you want to keep and cannot jsut get back out of the repo's (mostly your /home folder) then reinstall Ubuntu fresh. It will take a bit to reinstall all of the apps, but it is less risky. Far less risky. It would not depend on your second drive holding out, or a potential mistake breaking your Partition table.

---

### Post by fsmithred on 2008-03-16
(Note: I've never done this, either, but I have moved my /home to/from a separate partition, and I've moved whole installations to another drive. You might need to adjust the order or contents of these instructions.)

You can do it without gparted if you put your new /boot under /

Edit the fstab (comment out the line for /boot or edit it if you make a separate /boot partition). Edit the lines for any other partitions if you change their device names.

You might need to move the jumper on the drive so that it's master - take this into account before editing files. 

Edit your grub/menu.lst to point to the correct partition on the 'root' line if it's going to be different, and check some of the other options, like groot or kopt, to make sure they're right. Check your grub/device.map to make sure it's right. 
 
Install grub onto the main drive with grub-install /dev/whatever.

---

