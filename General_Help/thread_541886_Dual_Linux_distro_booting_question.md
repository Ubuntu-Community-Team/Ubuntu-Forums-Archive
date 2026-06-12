---
title: "Dual Linux distro booting question"
date: 2007-09-03
forum: General Help
---

### Post by Pharisee on 2007-09-03
I was wondering is it perfectly safe to have 2 Linux installs. I will basically install Ubuntu again on another partition, this install is where I attempt to destroy things :)

I am just curious if multiple reinstalls could effect my boot loader and therefore give me trouble loading into my everyday installation. Also I was wondering if after I am done playing is there a way to extend the partition back for my everyday installation to use?

Cheers.

---

### Post by sumguy231 on 2007-09-03
It's certainly possible, there's pictures somewhere of some guy's computer which has about 50 Linux distros on the same system. The new Linux distro will offer to overwrite your bootloader, of course - you can either do this, or leave Grub alone and add the boot entry for the new distro yourself later. The second option is probably only better if you know what you're doing.

---

### Post by strabes on 2007-09-03
You'll have to remember which partition has the config information for GRUB.

---

### Post by Pharisee on 2007-09-03
Which would be better in the long run, keeping my original boot loader, or allowing it to be overwritten? I understand the former would be harder, but if it's better I'll figure it out :) I just wish to avoid any possible corruptions from what I am guessing will be many reinstalls from playing around with the secondary install :)

Thanks guys!

---

### Post by rsambuca on 2007-09-03
I have seven different OS's on my rig, five of which are linux distros.  If you have one distro which you consider your "safe base", then I would recommend using that grub.  When you install another distro onto a different partition, make sure you direct the grub to the /boot folder of the NEW distro's partition.  Then add a chainloader option to the menu.lst of your original distro's grub.

Some people don't like this because you hop from grub to grub, but if you set the timeout option of the second grub to 1 or 2 seconds, you don't really notice it that much.  The benefit of this is that if the new distro updates its kernel, it will (usually) update its own grub automatically, so you never have to reconfigure any grub menu.lst files after the original installation.

To chainload to the new distro, just add the following to the bottom of your existing grub:

title     NEW DISTRO (call it whatever you wish)
root    (hd1,2)      <-- obviously change this to what the new partition is
chainloader +1

---

### Post by Pharisee on 2007-09-03
Awesome. I really appreciate the help, thanks. Just 2 last questions :)

1. Ubuntu will be my secondary installation, when I am installing it from the Live CD will it ask me automatically where I wish to install GRUB or must I do it manuall?

2. Since my primary installion is on "HD0,0" (I checked the menu.lst) would I be correct in guessing it would install on "HD0,1"?

Thanks!

---

### Post by ukripper on 2007-09-03
> **Pharisee said:**
> Awesome. I really appreciate the help, thanks. Just 2 last questions :)

1. Ubuntu will be my secondary installation, when I am installing it from the Live CD will it ask me automatically where I wish to install GRUB or must I do it manuall?

2. Since my primary installion is on "HD0,0" (I checked the menu.lst) would I be correct in guessing it would install on "HD0,1"?

Thanks!

Do manual install.

---

### Post by Pharisee on 2007-09-03
okay, thanks! :) Was I correct about where it would install the secondary installation?

---

