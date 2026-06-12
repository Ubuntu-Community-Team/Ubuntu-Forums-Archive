---
title: "Initramfs boot error"
date: 2013-02-12
forum: General Help
---

### Post by qazxsw21000 on 2013-02-12
> **kiyop said:**
> It seems like...
your kernel and initramfs were read and started, but cannot mount the correct root partition.

Boot with LiveCD and mount the partition where ubuntu was installed on, by clicking the proper partition from "Places"->"Removable media".

Open 
boot/grub/grub.cfg
or
boot/grub/menu.lst
and find the line starting with "linux" or "kernel".
Please post what comes after "root=", by openning this page with FireFox.
For example, 
root=UUID=*******************

"Application"->"Accessory"->"Terminal"
and execute the following command in the openned window.
```
sudo blkid
sudo parted -l
```Post the result, by openning this page with FireFox.
Sorry for asking for help on an old topic, but this follows very well with my problem. The OP stated my exact error. The quoted message is where things go terribly wrong for me. I looked in boot/grub for grub.cfg. And I do not have a grub.cfg. There is only one file in there named, "grubenv" with the contents:
```
# GRUB Environment Block
#######################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################################
```The very last thing I done was install updates (it was a 100% fresh install over the entire HDD) and install the restricted content package.

---

### Post by oldos2er on 2013-02-13
Post moved to its own thread.

---

### Post by qazxsw21000 on 2013-02-16
As a last resort I didn't want to take, but had to, I did the following:
I have an external HDD which I have the same system installed. I plugged it into the computer and left the live CD in the drive. I booted into the live CD and copied the contents of /disk/boot/grub into /boot/grub (I don't recall the drive directory).

After a reboot, it booted up fine. So I ran "sudo update-grub" so that a more proper grub.cfg would be made. I've not checked yet to see if it still works.

---

### Post by dino99 on 2013-02-16
otherwise simply purge grub-pc, then reinstall it on /dev/sda, and run again update-grub

---

