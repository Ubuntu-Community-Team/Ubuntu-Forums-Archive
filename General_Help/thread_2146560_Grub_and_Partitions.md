---
title: "Grub and Partitions"
date: 2013-05-18
forum: General Help
---

### Post by PJs Ronin on 2013-05-18
My expertise with Ubuntu/Linux is not good, but I'm trying to learn.

I have several partitions on my HD which are essentially grouped in pairs with a Ubuntu installation in each pair group.   The first partition in a pair is for '/' and the second is for '/home'.   
[IMG]http://i44.tinypic.com/eurr6f.jpg[/IMG]

As you can see from the image above, I am currently running the Ubuntu installation at sda5/6, which is my 'production' system based on Raring.   sda7/8 is a Saucy upgrade of Raring copied from sda5/6.   sda9/10 is a Saucy mini iso install with a bunch of Gnome thrown in (my disappointment continues).   sda11/12 is a daily CD install of Xubuntu Saucy. In each install, the Hostname is set as per the partition label, ie raring-a, saucy-a, saucy-b etc.   Occasionally, I end up in unfamiliar Linux territory, end up crunching things and have to resort to Boot-Repair to get me back to a bootable/workable system.   However, I am inexperienced with Grub and end up with a Grub list that looks like this:

[IMG]http://i44.tinypic.com/33bju2s.jpg[/IMG]

Even Xubuntu is being listed as Ubuntu.

What I would like is that on boot Grub would display the Hostname or the partition details instead of "Ubuntu Saucy Salamander etc etc".   My dream world is for a listing along the lines of:

Ubuntu Raring on sda5
Advanced Options for Raring on sda5
Ubuntu Saucy on sda7
Advanced Options for Saucy on sda7
Ubuntu Saucy on sda9
Advanced Options for Saucy on sda9
Xubuntu Saucy on sda11
Advanced Options for Saucy on sda11

I've read a couple of howtos on modifying grub and waded through the Grub manual, but this is a little beyond me.   Even Grub Customizer left me scratching my head.    Any/all suggestions would be appreciated.

---

### Post by oldfred on 2013-05-18
I have a lot of installs in my sdc drive. I keep /home inside my install and use data partitions for all my data. I am aggressive about moving data including some of the normally hidden files & folders like Firefox & Thunderbird profiles into my data partitions.

Then the first thing I do is turn off os-prober and copy my 40_custom into my new install. Edit for a new partition. I boot partitions as I learned from Ranch Hand, but cavsfan document that plus some other grub customization.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

      
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

     You can put any description you like and can boot one older kernel also as the link is backed up as .old at the end.

 #Add menu entry to 40_custom, change example from sda13 to your partition.
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub
sudo dpkg-reconfigure grub-pc
Or
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub

---

### Post by PJs Ronin on 2013-05-19
> **oldfred said:**
> I have a lot of installs in my sdc drive. I keep /home inside my install and use data partitions for all my data.

Yeah, I am slowly coming to the conclusion that that's a better way to operate.   I'm starting to understand that '/home' really doesn't do a heck of a lot except for some local customization so I may start changing to a single '/' for each install for everything except data.   Like you, I also have a separate data partition (on a separate HD) which really saves a lot of time/effort when bedding in a new distro.

Thanks for the links... time to do some more reading :)

---

### Post by PJs Ronin on 2013-05-19
Pretty happy camper right here folks, and I've only read the first link.   Thanks Fred.

[IMG]http://i41.tinypic.com/3523hjo.jpg[/IMG]

---

