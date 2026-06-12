---
title: "Loads of problems, I'm assuming they have a commmon source."
date: 2013-02-13
forum: General Help
---

### Post by Superoo7 on 2013-02-13
I've been running Ubuntu for almost a year, but never run into something like this.
I  must admit I'm probably not as Ubuntu savvy as I should be after a  year. If anyone of you can help me out, that'd be greatly appreciated! I'm running 12.04.

I have a plethora of problems that all started in the past two weeks which leads me to believe they're related.
To start when I start up my Laptop I get a screen saying
 "Realtek PCIe GBE family controller series v2.44 date
PXE-E61:Media test failure, check cable
PXE-M0F: exiting PXE ROM
reboot and select proper boot device"

If I don't get that screen I always get a screen saying
"Disk drive error
Error found while checking disk drive for /"
I press "I" to ignore and continue on

Once I'm actually in and running after a few minutes all of my folders will become read-only, stopping me from moving files, downloading, etc.
Originally I could log out and back in and it'd be back to normal. Now when I log out it takes me to a blank black screen with text.

There seem to be lots of other tiny things as well. So do all of these have a source, or did my Laptop go to **** all at once?  suggestions/fixes are greatly appreciated!

---

### Post by JiuJitsu500 on 2013-02-13
The PXE ROM thing comes from a network boot failing, since your OS is not on any network. This also incresess boot time. Go into your BIOS and disable the network boot device to stop that issue.

Chances are for the rest of your issues, just ensure that your HDD is the first boot device in the BIOS, that should clear a lot up. I doubt it'll do everything, but should clear some things up.

After that, post results - and some boss will fix this nonsense! :)

EDIT ** Oh, hold left SHIFT I think while booting to get into GRUB, and boot into recovery mode, then enable networking. From there choose "fix broken packages" and let it do it's thing. If you're on ethernet, you should be okay - I don't know how to do it wirelessly, but it may connect automatically. Don't quote me. Once dpkg configures, drop into the root shell and type without quotes: "apt-get update && apt-get dist-upgrade" to ensure your system is fully updated. Then reboot...

Skip the update process for less risk or you have no internet connected. Dpkg will work better with internet as it can correct everything with updated package information, etc...

Worse case scenario, your HDD is boned. I'd hate to be the bearer of bad news, but just for reference - how old is this rig?

---

### Post by QIII on 2013-02-13
If you have not done anything to your BIOS before, it is possible your drive is failing or has been jangled loose.

If your BIOS settings are correct, try (carefully!) reseating your drive.

---

### Post by Yellow Pasque on 2013-02-13
Backup your data, if possible... NOW

---

