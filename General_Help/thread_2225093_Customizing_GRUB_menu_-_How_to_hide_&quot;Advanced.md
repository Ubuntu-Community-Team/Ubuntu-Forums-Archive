---
title: "Customizing GRUB menu - How to hide &quot;Advanced Options&quot;?"
date: 2014-05-19
forum: General Help
---

### Post by Remten on 2014-05-19
How to hide the specific menu entry of "Advanced Options for Ubuntu" which is displayed on the grub menu? (What code to use? I don't want to use grub-customizer package to do this.)

I have a single hard drive, containing several partitions, with two OS's - Windows and Lubuntu 14.04, 3.13.0-24.
I just want those two options showing on the menu.

(The grub, version 2.02, menu works fine now, but I want to tweak its appearance.
I'm already using code such as
```
sudo chmod -x /etc/grub.d/20_memtest86+
``` to deactivate/hide certain grub menu options.)

---

### Post by oldfred on 2014-05-19
When I manually install grub to my flash drives, it has no os-prober or any scripts and I have to manually create my own grub.cfg. Originally I copied from known working boot stanza.

Post by Ranch Hand on turning off scripts:
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)
> Well, if you have three OS' on your drive and you set up a custom menu  you do not need any other menu entries at all. So you change the  permissions on 10_linux, 20_memtest86+, 30_custom so that they are not  executable. They will not run when &#8220;update-grub&#8221; is run and so the onoy  thing on your menu is your custom entries. There is nothing that can  mess with these entries except you.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

      
 Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

### Post by Remten on 2014-05-20
Thanks for the reply, Fred. I turned off some of the script components but I am hoping to avoid completely eliminating the scripts because I don't want a huge hassle every time I get a kernel upgrade.

But I think after playing with it for a few hours I've found how to tweak the grub, through a somewhat convoluted manner.
Will need to do some more testing. I'd rather not mark the thread closed as yet, in case someone else has a simple easy suggestion.

---

### Post by Remten on 2014-05-20
Addendum:  Maybe I should note that I completely understood the tweak suggestions in the [Grub 2 Title Tweaks blog post]("http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html") linked to from Dedoimedo's old Grub2 tutorial. The problem is that the code for the sections I am interested in has been significantly changed (*from a novice's perspective*) between that version and the current 2.02 version, which has caused me a fair bit of confusion. I think I've sorted it out.
Just wondering if there's an up-to-date tutorial, or non-technical explanation of the new changes somewhere that would be similar to those older articles.

---

### Post by oldfred on 2014-05-20
I so not like editing the scripts.

But I just create one boot stanza that will boot the most current kernel. It is in the Cavsfan thread as he better documented instructions we learned from Ranch Hand.

       I first saw this from Ranch hand - I think he was testing daily, so kernel could change a lot:
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
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

---

