---
title: "Ubuntu 15.04 hangs on shut down"
date: 2015-11-04
forum: General Help
---

### Post by acerspyro2 on 2015-11-04
Hello, I usually do not ask on forums for help as I search online first and almost always find a solution to my problem, but I'm stuck here.

This is a month-old install of Ubuntu 15.04 (Originally Kubuntu, but everything KDE-related has been purged, as I use the GNOME desktop now. Installed via the minimized net installer.) on a Lenovo ThinkPad T400 (120GB SSD, 4GB DDR3, ATI Radeon HD 3470, Core 2 Duo).

Upon installing the system, I decided to install FGLRX. MEEP-WRONG. No legacy FGLRX support for Ubuntu 15.04! (Which is required for HD 4xxx and <). So I went ahead and purged it from my system. After I did so, my system would always hang on shutdown. REISUB didn't do anything, I have to hold down the power button for it to shut down. Also note that hard drive activity is always at 100% while it hangs on shut down (This also seems to trigger some sort of whistling sound out of the laptop when disk activity is high. I have an SSD. Failing capacitor?). I have also tried purging FGLRX from Xorg.conf files, see if Xorg was freezing the system by trying to unload a non-existing driver, no luck there. Nothing shows up in the logs either (unless I am missing some?), and when I start up my system again, I am presented with a SWARM of "System problem detected" windows. They don't contain any useful information (They contain messages about the computer not being shut down properly).

I hope to fix this problem before I end up corrupting my system for good.

---

### Post by ajgreeny on 2015-11-04
It sounds as if the OS has shut down fully but the computer is not carrying out the final power-off, so if that is the situation you are very unlikely to corrupt the system files.  It would, however, be good to get it powering off properly.

Does it shutdown properly if using the terminal command ```
sudo shutdown -h now
```

---

### Post by acerspyro2 on 2015-11-04
Just tried it, still hung. Also, it's still in the OS when it hangs, since it complains about not being shut down properly on start-up.

---

### Post by ajgreeny on 2015-11-04
Yes, I've just re-read your post and noticed that.
Have you totally removed the current /etc/X11/xorg.conf file if you still have one?  If not do so with ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` which will rename it as a backup in case you need it for any other details.

Do you have both an SSD and a HDD?

---

### Post by acerspyro2 on 2015-11-05
Sorry for the delay. First of all, no, my laptop only has an SSD in it, no HDD. Second, my system has no trace of any xorg.conf file. Everything that is related to configuring Xorg is in /usr/share/X11, and I checked all the files in there: no mention of FGLRX anywhere. Even grep'd the whole directory.

---

### Post by ajgreeny on 2015-11-05
OK; it's a different version, and DE, but the same apparent problem, with several solutions suggested, and in some cases working.

Have a good read through and see if any of these help you shutdown properly.
[http://ubuntuforums.org/showthread.php?t=2220591](http://ubuntuforums.org/showthread.php?t=2220591)

---

### Post by acerspyro2 on 2015-11-06
Thanks for the link! Adding "acpi=force" to my grub config did the trick! No more hanging! iei

---

### Post by acerspyro2 on 2015-11-07
It shut down correctly one time, probably by luck. Then, it started doing it again. Also, I found some strange verbose/debug stuff in my dmesg that I'm not sure I have seen before.

dmesg log: [http://paste.ubuntu.com/13159249/](http://paste.ubuntu.com/13159249/)

Edit: Attempting BIOS update, my firmware is very old, and looking at the changelog for this BIOS's updates, it does mention 
 - (Fix) The computer may hang after graphics mode changing and reboot.

As well as

 - (Fix) Fixed an issue that might cause reboot failure.

---

