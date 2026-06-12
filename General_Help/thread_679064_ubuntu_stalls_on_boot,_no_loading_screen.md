---
title: "ubuntu stalls on boot, no loading screen"
date: 2008-01-26
forum: General Help
---

### Post by JohnnyBoy022 on 2008-01-26
I have been running Ubuntu off of an external hard drive for the past two weeks, and everything has been fine. One problem was that it never showed the loading bar when booting up. It went straight from grub to a black screen for about a minute then to the gnome login.

Now something has gone wrong. I see the "Loading please wait..." and the black screen like normal. Then my wifi light starts flashing about every second, and nothing else happens. I have no way of knowing where it is stalling because the loading bar doesn't show up.

Is there any way to boot into Ubuntu with the text in the background that shows what is happening so I can figure out what is going wrong? Also what does safe mode do? Thanks for any help.

---

### Post by eapache on 2008-01-26
Safe mode only boots part way and then drops you to an admin terminal.

To boot with the text background, select the ubuntu menu item in grub, but then press 'e' instead of enter. Now scroll down to the line that starts with /boot/vmlinuz and press e again. Scroll to the end of the line and delete "splash" and "quiet". Press enter to save the line, and then enter again (I think, it might be "b", check the bottom of the screen) to boot. This will show the text, and hopefully where it is failing.

---

### Post by JohnnyBoy022 on 2008-01-26
Thanks, I will try that out and post back here

---

### Post by JohnnyBoy022 on 2008-01-26
Well I am back in Linux world now. I tried what you said and i didn't have an option for splash (that explains why it never showed up earlier). I disabled quiet, didn't help. I tried recovery mode, and i got the message "/dev/sdb1 (my external) has been unmounted 30 times - checking force" and it sat there for a few minutes. After that I was able to log in just fine. Anyone know what this message means, for future reference?

---

### Post by eapache on 2008-01-26
Ubuntu automatically checks your hard drives for errors every thirty boots regardless of the mode you start in. This is in order to help prevent hidden data corruption. If you want to configure these further (and tell it to check on shut-down instead of boot, which I find nice), try AutoFsck at

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

The FileSystemChecK shouldn't be related to your problem. In recovery mode, try running```
sudo dpkg-reconfigure -phigh xserver-xorg
```and then reboot into normal mode. This will reset your graphical configuration file.

---

### Post by JohnnyBoy022 on 2008-01-27
Thanks for the info.

---

### Post by linuxisfree on 2008-01-27
> **JohnnyBoy022 said:**
> Well I am back in Linux world now. I tried what you said and i didn't have an option for splash (that explains why it never showed up earlier). I disabled quiet, didn't help. I tried recovery mode, and i got the message "/dev/sdb1 (my external) has been unmounted 30 times - checking force" and it sat there for a few minutes. After that I was able to log in just fine. Anyone know what this message means, for future reference?

try looking at this to fix your settings:D

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

