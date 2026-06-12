---
title: "Ubuntu 14.04 not booting (kernel panic?)"
date: 2014-06-04
forum: General Help
---

### Post by Alexander_Ryan on 2014-06-04
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I've already installed ubuntu 12 alongside windows 7 before on this computer and it worked perfectly. I've since completely wiped the computer and reinstalled windows 7. However, this time when I try to boot ubuntu 14.04 that I installed from a live usb it just gets stuck during a kernel panic. Here are pictures of it happening: [/COLOR][http://i.imgur.com/rzm7kFg.jpg](http://i.imgur.com/rzm7kFg.jpg)[COLOR=#000000] and in recovery mode: [/COLOR][http://i.imgur.com/EW9iZkd.jpg](http://i.imgur.com/EW9iZkd.jpg)

[COLOR=#000000]I've tried recovery mode but the same thing happens. I tried boot repair disk from a live usb but it didn't change anything. I then made a bootinfo summary that can be found here: [/COLOR][http://pastebin.com/K5ZhCzRa](http://pastebin.com/K5ZhCzRa)

[COLOR=#000000]I don't know what to do. I've heard about something called grub but I have no idea what it is or how to use it.[/COLOR]
[COLOR=#000000]I have no idea what to do anymore. [/COLOR]

[COLOR=#000000]Thanks in advance.[/COLOR]

[COLOR=#000000]P.s. I've already asked this on askubuntu.com but it didn't really help: [/COLOR][https://askubuntu.com/questions/4758...b-kernel-panic]("https://askubuntu.com/questions/475879/ubuntu-not-booting-after-install-from-usb-kernel-panic")

---

### Post by oldfred on 2014-06-04
Are you booting with Intel internal video or nVidia? Can you set which or is it automatic?

Video could be part of issue. nomodeset works with nVidia, options by  ubfan1 often work with Intel internal video or others.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

