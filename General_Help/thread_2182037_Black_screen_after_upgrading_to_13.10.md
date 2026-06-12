---
title: "Black screen after upgrading to 13.10"
date: 2013-10-19
forum: General Help
---

### Post by euphgeek on 2013-10-19
I just upgraded to Ubuntu 13.10 and all I get is a black screen.  If I press Ctrl+Alt+Backspace, the login screen displays just fine.  I've tried all the different session types and all I get is a black screen.  If I do startx from a command line, it gives me the error message "ERROR: could not insert 'nvidia_319': No such device".  I made sure the package nvidia-319 is installed.  I even tried using a different driver, fglrx, which I've used in previous versions, but no luck.  I'm using the 64-bit version if that makes a difference.  Anyone have any ideas on this?

---

### Post by rihikz on 2013-10-19
Unless this is a well known bug/problem, I don't think you have a better option than just reinstalling Ubuntu.

---

### Post by QIII on 2013-10-19
Hello!

Which of the two do you have: An NVIDIA card or an ATI card?  If you have an NVIDIA card, installing the ATI driver (fglrx) would at best do nothing and at worst make things unusable.  The drivers are not interchangeable.

Did you have a proprietary driver installed when you did the update?  If so, that is one of the quickest ways to make your upgrade a significant emotional event.  Proprietary drivers should be uninstalled prior to upgrades.

Before you do anything like reinstalling, first try to uninstall the proprietary driver from recovery -- or both if you now have both installed.  If you can do that, you will be able to boot with the open source driver for whichever card you have.

Cheers.

---

### Post by euphgeek on 2013-10-19
> **QIII said:**
> Hello!

Which of the two do you have: An NVIDIA card or an ATI card?  If you have an NVIDIA card, installing the ATI driver (fglrx) would at best do nothing and at worst make things unusable.  The drivers are not interchangeable.
I have an onboard video card that, if I remember correctly, is an ATI  card.  I have been using nvidia drivers for at least a couple of the  previous releases after the fglrx driver stopped working.  I think I may  have looked it up and found that it has an nVidia chipset or something  like that.  It was a long time ago. Edit2: lspci -v reports that it's a Radeon HD 4200.
> Did you have a proprietary driver installed when you did the update?  If so, that is one of the quickest ways to make your upgrade a significant emotional event.  Proprietary drivers should be uninstalled prior to upgrades.
Yes I did. :(
> Before you do anything like reinstalling, first try to uninstall the proprietary driver from recovery -- or both if you now have both installed.  If you can do that, you will be able to boot with the open source driver for whichever card you have.

Cheers.
Installing one driver automatically uninstalls the other, so I only have one installed.  I wasn't able to remove the nvidia-319 package from recovery mode, so I removed it in regular mode.  After I rebooted, everything came up for me as normal.  So I guess I'll just keep using whatever open source driver I'm using.  Edit: according to lspci -v, it's using the radeon driver.

---

### Post by QIII on 2013-10-19
Depending on how you install them, the other may not be installed.

The Nvidia driver will not drive the ATI GPU and should not be installed.

The reason the ATI card will not work with the proprietary driver is that it is a legacy card.  Cards prior to the HD 5000 series have been forked to a legacy driver branch.  That driver will not work with X Server in versions of Ubuntu beyond 12.04.1.  It would have worked with prior versions of Ubuntu, but not 12.10, 13.04 or 13.10.

You did well to remove the NVIDIA driver and now should rename or remove /etc/X11/xorg.conf.  The open source Radeon driver for ATI cards does not need an xorg.conf and having one may cause errors if it contains instructions suitable for other drivers.

Because your legacy card will not work with any proprietary driver, you should simply use the default open source Radeon driver.

---

### Post by euphgeek on 2013-10-19
OK, I removed the xorg.conf.  Thanks for your help.

---

