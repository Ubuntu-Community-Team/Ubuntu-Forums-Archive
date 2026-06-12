---
title: "No Graphics Drivers Listed In Additional Drivers PLUS Manual Installation Problems"
date: 2013-08-01
forum: General Help
---

### Post by shabalabadingdong on 2013-08-01
I have just installed Ubuntu on my Desktop Computer, and it's pretty fast.  My computer is even 5 years old.  But I really want to play some high quality games, and I need to install the graphics card drivers required, they do not show up on the Additional Drivers tab, and I have tried this [http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/](http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/) which once I run the command sudo sh ./amd-catalyst-version-here-and-such.run --buildpkg Ubuntu/raring(Which is replaced by the actual file name.)
  
in the terminal it says that I need an extra package or program to continue installation and it stops.  Is there any other way to install the proprietary graphics card drivers, or any fix on the manual installation problems.  The two commands before the run command in that link are already installed is there a possible way to take them out and reinstall them, and then continue with the run command without any problems?

They are 
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot libqtgui4 devscripts

and


sudo apt-get install lib32gcc1



My Graphics Card - **Gallium 0.4 on AMD RV635** (which I think is the equivalent of the **ATI Radeon HD 3000 series**...I think...)


**Thanks for any help!**

---

### Post by Paww on 2013-08-01
You could uninstall them and uninstall them I guess. But did everything look ok when you installed them? Maybe the problem is somewhere else. Maybe you need build-essentials and/or linux-headers?

---

### Post by shabalabadingdong on 2013-08-01
> **Paww said:**
> You could uninstall them and uninstall them I guess. But did everything look ok when you installed them? Maybe the problem is somewhere else. Maybe you need build-essentials and/or linux-headers?

Probably.  I know this is a noob question but how do you uninstall them?  Do you uninstall them with Synaptic?

---

### Post by SweetAurora on 2013-08-01
I see your Graphics card is an HD3000. Be aware **EVERY **ATI graphics card **EVER MADE **before the ATI HD5000 series **IS NO LONGER SUPPORTED BY ATI.** They have been placed in legacy and are not updated in linux. Like it or not, if you have one of those older ATI cards, you are stuck on the open source driver and you can't do any serious gaming. Sorry.

Edit: Even if you compile the driver from source, it still wont work. All the newer versions of the Catylist Suites do not contain driver support for older cards.  And you can't use an older version of the suite either. The Kernel, MESA Version, and X.Org version are too new for the older suites from ATI. You can try installing one of the original copies of Ubuntu 12.04 (12.04.0 or 12.04.1). They support those graphics cards and older suites still.

---

### Post by shabalabadingdong on 2013-08-01
> **kitsuneinari78 said:**
> I see your Graphics card is an HD3000. Be aware **EVERY **ATI graphics card **EVER MADE **before the ATI HD5000 series **IS NO LONGER SUPPORTED BY ATI.** They have been placed in legacy and are not updated in linux. Like it or not, if you have one of those older ATI cards, you are stuck on the open source one and you can't do any serious gaming. Sorry.

Edit: Even if you compile the driver from source, it still wont work. All the newer versions of the Catylist Suites do not contain driver support for older cards.  And you can't use an older version of the suite either. The Kernel, MESA Version, and X.Org version are too new for the older suites from ATI. You can try installing one of the original copies of Ubuntu 12.04 (12.04.0 or 12.04.1). They support those graphics cards and older suites still.

Guess I can't do any serious gaming then, I am thinking about getting the AMD Radeon HD 7770 Graphics card anyway, but anyway thank you very much!

---

### Post by Bashing-om on 2013-08-01
shabalabadingdong' Hi !

I am aware of 1 likely alternative to use proprietary drivers with that graphics card. One must install the legacy version of 12.04.1 ....
[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)
However, a better card is always a better solution.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by MIJ-VI on 2013-08-01
"RV620/RV635 - Radeon HD 3410/3430/3450/3470/3650/3670"

RadeonDriver - Community Ubuntu Documentation
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Scroll down to "Older RadeonHD (Catalyst Legacy 13.1 & Open Source)"

Hardware - cchtml.com
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

Howto install ATI Display driver in Ubuntu | Unixmen
[http://www.unixmen.com/howto-install-ati-display-driver-in-ubuntu/](http://www.unixmen.com/howto-install-ati-display-driver-in-ubuntu/)

FWIW I believe that Linux Mint 13 (MATE is the fastest UI) still supports and will install the AMD Catalyst™ Proprietary Display Driver for Radeon HD 3000 series graphics cards.

---

