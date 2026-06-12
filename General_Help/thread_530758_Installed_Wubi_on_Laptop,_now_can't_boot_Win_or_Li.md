---
title: "Installed Wubi on Laptop, now can't boot Win or Lin"
date: 2007-08-20
forum: General Help
---

### Post by neodorian on 2007-08-20
I had been using Wubi on my Tablet as a secondary OS since I liked having Linux on my desktop but the Tablet does not have a CD drive so I had no way to install it easily.  I had messed around with it for a while but today I decided to reinstall with the UbuntuStudio version just for something new to fiddle around with.

I completed the install and got to the initial screen where I would normally log into Ubuntu.  For some reason it wouldn't accept my login/pass so I figured that maybe I had entered it wrong when I installed it.  No biggie...I would just hop back into windows and either see if I could figure it out or at worst, reinstall it since it was a fresh install anyway.

When I rebooted, I got an error that flashed up quickly and I believe it was that it couldn't find NTLDR but it's pretty quick so I can't really see.  It then tries to boot windows from c:/windows/ but it bluescreens right after the WindowsXP screen comes up.  I tried booting to a command line but it still BSOD right after giving the option to hit esc to skip sptd.sys.  I tried it with skipping it and not skipping but either way it won't get past without a BSOD and immediate reboot.  

This whole thing is confounded even more by the fact that I have no cd drive on this tablet, nor can I boot to a typical usb external because Toshiba is run by jerks who build laptops that will only boot to their drives and a few select others ;)

Just looking for any hints.  It seems I might be stuck here until I shell out for a CD drive.  The laptop is a Toshiba Portege M200 which was running flawlessly up until today.

---

### Post by ago on 2007-08-21
If you hard reboot, you need to run chkdsk /f from windows, since hard rebooting can co rrupt ntfs.

For the rest you should use the latest version available from the website, which at the moment is 7.04.04. Login should be ok with that.

---

### Post by neodorian on 2007-08-21
Yeah, it was the newest version and the one I had used successfully before.  I think if anything I just made a user error when it came to defining the login/pass.

My problem is that with this laptop, there is no optical or floppy drive to boot to and run chkdsk.  I think I can make a bootable floppy image on an SD card and boot to that so that's probably my next thing to try.

---

### Post by neodorian on 2007-08-23
Solved!

I gave up trying to get this thing to boot properly from assorted devices.  Eventually I just took out the hard drive, hooked it up to my desktop as an external USB drive and ran chkdsk from there.

Thanks for the help!

---

