---
title: "fixing Grub2 after fsarchiver restfs borks it on multiboot systems"
date: 2014-03-01
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-03-01
When fsarchiver is used to restore a system to a partition of a multiboot system often the archive may have been made on a system with a different partition setup, a different number of bootable partitions, etc., etc., and, not surprisingly, grub2 can be totally and weirdly borked. I did it recently and gparted, looking at it from a live cd, claimed that 2 partitions were both mounted as /.  When I booted from the hard drive grub showed 2 bootable partitions, one of them on sda1 and one on sda2, which was as it should have been, but selecting either booted the sda1 system.  I've repartitioned since and that particular incarnation of sda2 is gone, and I got a sane grub2 by installing a simple tty-only system on a logical sda7. But I have more partitions to play with, and more archived systems I can restore, so here is the general question:

If I restore a system to a partition of a hard drive while booted from another partition of the same drive, would it be reasonable to assume that if I were to```
sudo apt-get install grub-pc
sudo update-grub
```(adjusting grub version as appropriate for the particular hardware and preference) before shutting down or rebooting that I'd have a functional grub, maybe without the same font size, default partition, etc, but nonetheless a working grub reflecting the reality of the system? And that this would be true regardless of what partition had grub before? I was thinking of putting those commands at the end of my fsarchiver-restore script.

Alternately, if I chroot into another partition that contains a bootable system, and run the same commands there, that it would work the same but with that partition as the default to boot from? Is that a reasonable expectation? Put more generally, in a multiboot system, should it be possible to run those commands on any debian family system and get a new grub menu with that system as the default to boot?

This is not a crucial matter - if need be I can determine these things by experiment and in the worst case, I can always get a working grub by the inelegant method of installing a minimal tty only system on still another partition, but it would be nice to do it more elegantly and quicker.

Thanks for your time.

---

### Post by oldfred on 2014-03-01
Not sure at what level fsarchiver is working. It it also copies UUID, not just files you have to change UUID, reinstall grub2, edit fstab and maybe other changes with new UUID.

If it copies files only you still have to reinstall grub2 and edit fstab with new UUID.

Since you can only have on install's grub2 in the MBR, that is the system in control and that you boot with. It will be first in boot menu and a sudo update-grub should add other systems. But any update to kernel in other system requires two sudo update-grubs. You have to run it in your updated install to get grub.cfg updated and then boot into the default system and run sudo update-grub. It reads the grub.cfg by default in other installs so if they are not updated, it will not include new kernels. But there is a work around.

You can boot a partition not a specific kernel with Ubuntu. Ubuntu has links in / to the latest kernel. And you just specify those links as boot and will then boot most recent kernel in that install.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

I turn off os-prober, and add entries to 40_custom.
      
 #Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub


 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}
```

Each install may be set to auto reinstall grub to the MBR on major updates. You may want to unselect that so that it does not reinstall.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

If you unchoose all options it should not reinstall.

---

### Post by Dreamer Fithp Apprentice on 2014-03-01
Thanks, Oldfred. That's pretty comprehensive. Much more to the subject than I thought. I'll be studying this for a while but I think I've already gotten enough of it to make practical use of it.

---

