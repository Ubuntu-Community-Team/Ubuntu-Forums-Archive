---
title: "How to customize grub entries"
date: 2013-03-18
forum: General Help
---

### Post by Luca Borrione on 2013-03-18
Hello,

I installed lubuntu 12.10, ubuntu 12.10 and kubuntu 12.10
Usually I use lubuntu but I want to practice the other flavors as well :)

Now grub lists them all as Ubuntu 12.10
How can I edit grub in order to distinguish the flavor?

Thanks

---

### Post by Dennis N on 2013-03-18
This documentation explains how to make a custom menu:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Note: I used this guide, and it works well.

Good luck.

---

### Post by oldfred on 2013-03-18
You can use grub customizer.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

But with normal grub2's os-prober and multi-booting you have to boot into any second install and update it, then boot in current install that is in MBR and update it to find the updates in the second installs.
I prefer to just add default entries which I can name anything I want and boot those.
Documented here, but details are about halfway down.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

An entry like this in 40_custom works.

      
 #Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc

   I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

