---
title: "Bypass bootloader after hibernation"
date: 2007-11-23
forum: General Help
---

### Post by varchar255 on 2007-11-23
Is there a way to bypass the bootloader after hibernation?

I have a dual-boot machine running Windows and Ubuntu with the Windows bootloader. If I hibernate Windows, the bootloader loads Windows immediately without a prompt. This behavior is what I want when hibernating Ubuntu as well. I don't care whether it's GRUB or the Windows bootloader as long as whichever OS I hibernate runs immediately after power on without showing the bootloader at all.

The closest option in GRUB I've found so far is setting the default so that the last OS loaded is selected by default but that's not what I want, because it will select the OS even if it was shut down properly. I want it to be selected *only* if it was hibernated, or better yet, loaded immediately w/o showing the bootloader.

Essentially I want the opposite of what's described here: [http://forums.suselinuxsupport.de/index.php?showtopic=62137&st=0&p=252311&#entry252311](http://forums.suselinuxsupport.de/index.php?showtopic=62137&st=0&p=252311&#entry252311). That person wanted to enable GRUB after hibernation; I want to disable it.

The reason I ask is because I have accidentally booted into Windows while Ubuntu was hibernated and if you edit anything on an NTFS partition when that happens, your files get corrupted. If anyone can suggest a way to avoid that, that would be excellent.

Thanks for any help!

---

### Post by hikaricore on 2007-11-23
This isn't really possible or adviseable.

When you hibernate the boot loader doesn't even come into play.  The system state is stored in memory and loaded back from memory after words.

You really really really should be shutting the system down/rebooting when dualbooting and sharing drives between to OSes.
The alternative is unsafe at best and just plain silly.

---

### Post by varchar255 on 2007-11-23
Thanks for the incredibly quick reply!

I don't fully understand how the hibernation process works so please forgive me if I'm saying something ignorant, but apart from the danger of running one OS while the shared drive is hibernated on a different OS, what's wrong with hibernating while dual-booting? As long as you always run the same OS that was hibernated and reboot or shut down before switching, it should be ok, right?

I get what you're saying about the boot loader not coming into play when you hibernate, but how does the Windows bootloader do it then? There must be *something* that tells it "Windows is hibernated, restore it instead of loading bootloader" or I wouldn't get the behavior I see. I was hoping there's a Linux alternative that can do the same...no?

I definitely realize the risk in what I'm doing and the potential of corrupted drives, but being able to hibernate is so much faster than shutting down that I really hope this is possible, or at least there's a better workaround. When I'm using GRUB on another machine, I have to remember whether I hibernated the last time I used the OS which, as you said, is very unsafe.

Thanks!

---

### Post by hikaricore on 2007-11-23
If you're only using the one OS durring hibernate it is just fine, however I thought you were asking about switching between them in between hibernate and wake sessions which is a no no.

As far as bootloaders are concerned, I can almost assure you that a bootloader is never involved in the process of hibernation as the hybernation functions are in most cases native to the operating system.  You may see what appears to be a bootloader in the ***dows environment when returning from hibernate, but I don't believe that it actually is what it seems.

This Wikipedia article can probably explain the hybernation process better than I am able to:
[http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29](http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29)

---

