---
title: "Problem with grub2 --unrestricted boot for overlayfs rooted system"
date: 2014-04-02
forum: General Help
---

### Post by talfar on 2014-04-02
Hi,

I'm having a really strange problem on the system I'm trying to setup as open accessible webkiosk for the students at our school.
I installed a minimal trusty system, with plain Xorg-xserver running chromium-browser as single app, started automatically after an autologin. To avoid problems with students messing up the system, I made the rootfs readonly with an overlayfs masked tempfs. Everything fine so far. 
To prevent that someone can interfere with the boot process, I setup password protection for grub2 and marked the default menuentry as --unrestricted, so the system can boot unattended by bios wakeup. 
My problem is, that grub doesn't boot the default menuentry when the overlayfs readonly root AND the password protection is activated. Turning off the overlay root fs and with password protected grub, it boots as expected. Without the grub superuser the default menuentry is booted to the overlayed rootfs. Just the combination won't  work. Grub stops at the grub menu and doesn't show the timeout counter to boot the defualt menuentry. Just hitting return, boots the system without authentication.

I hope soemone can help me with my problem!

Best regards,

A.F.

---

### Post by oldfred on 2014-04-02
I have not done kiosk, but have some older links. Not sure if any are now useful as you now are using 14.04 which is not even released yet.

Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=2113023](http://ubuntuforums.org/showthread.php?t=2113023)
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/](http://www.alandmoore.com/blog/2011/11/05/creating-a-kiosk-with-linux-and-x11-2011-edition/)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)
[http://spins.fedoraproject.org/kiosk/#home](http://spins.fedoraproject.org/kiosk/#home)
Older
[http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/intro.htm)
[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition)

---

