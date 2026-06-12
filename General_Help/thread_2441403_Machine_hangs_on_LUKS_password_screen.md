---
title: "Machine hangs on LUKS password screen"
date: 2020-04-23
forum: General Help
---

### Post by solly9billion on 2020-04-23
I have a machine running Ubuntu 16.04 LTS which was no longer running correctly, on inspection it was identified that the boot partition had run out of space due to it filling up with new iterations of the kernel.  Autoremove wasn't working so I had to clean this up manually, so I removed the kernels it wasn't running taking care not to remove the one it *was* running.  I then restarted the machine, it looks like it is working fine and then when the LUKS password screen appears I cannot type the password, machine is totally locked up, numlock and scrolllock keys do not change the lights on the keyboard, esc doesn't have any effect, nor does ctrl-alt-del - the only way to get out is to hold down the power button on the case.

I've tried adding the nomodeset command in case it was a graphics driver issue, it get to the same place and hangs.

Booting in Recovery mode makes no difference.

I can boot from a live cd, unlock the drive with sudo cryptsetup open --type luks /dev/sda5 crypto_LUKS
mount the folders and chroot

And the run updates etc, but even after doing all that, when i take out the live CD and boot again it still only gets as far as asking for the LUKS password and everything being completely unresponsive.  I've been going round in circles trying to get this system working for a few days with no progress so I thought someone else might know where I'm going wrong.  I should warn you I'm quite a linux noob so apologies in advance if I says something that doesn't make any sense!

Dan

---

### Post by TheFu on 2020-04-23
Can you go into the Advanced Boot screen and see some kernels there? Do any of those work?

How did you remove the kernels?  Did you use apt or apt-get or dpkg 
or 
did you just delete the files without letting the package manager know?

Before you do anything else, you should make backups of all data and settings you don't want to lose.  Sometimes when encryption is involved, the easiest answer is to flush everything and do a reinstall after verifying that the HW isn't failing.  If the LUKS header is corrupted, that is usually the only solution.  I do NOT think the LUKS header is corrupted here, but that could happen at any point with storage, right?

In the list at the top of this post, if you did the removal using rm, then your package manager is out of whack and that needs to be corrected. Since you are new, fixing it will take longer than just doing a reinstall and restoring data.  Probably a good time to move to 18.04 or 20.04 while you are at it.
If the package manager was used to clean up kernels, just need to boot from the live CD, manually unlock the storage, setup a chroot using the LVM LVs (I'm assuming there are LVM LVs involved), then run update-grub so whatever remaining kernels can be found and setup in the boot.

---

### Post by solly9billion on 2020-04-28
I did try to use apt-get autoremove to remove the unneeded kernels but that wouldn't complete so I eventually had to resort to the rm method ([https://www.linuxuprising.com/2019/06/how-to-free-up-space-in-boot-partition.html](https://www.linuxuprising.com/2019/06/how-to-free-up-space-in-boot-partition.html)).  Initially I assumed it was the keyboard driver so I added hid usbhid hid_generic and ohci_pci to the /etc/initramfs-tools/initramfs.conf and then ran:

update-initramfs -u 

But like everything else, it hasn't made a blind bit of difference.

As much as I would like to just start from scratch there is a custom application on the machine that I didn't setup (Joomla based) which I'm trying to get back to.

The LUKS volume is not corrupted insofar I can unlock it with the the password when I boot from a live CD and the directories/files appear okay within it.

Nothing I'm doing now seems to let me get the system to boot without using a live cd, but I'm open to suggestions.

---

