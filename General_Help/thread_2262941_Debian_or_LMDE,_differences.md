---
title: "Debian or LMDE, differences"
date: 2015-01-28
forum: General Help
---

### Post by UDroidie626 on 2015-01-28
Okay so I want to move from Ubuntu to another distro, I need apt for uni, but I need more stability than messing around, but I want a newer kernel and slightly newer packages, but I just cant seem to like Ubuntu, I want to but I just cant, so what are the differences between these two?
I would ideally like to be on rolling over frozen system, but I will be on frozen if need be.

Thanks!

---

### Post by grahammechanical on 2015-01-28
As I understand things from just doing a little internet research, Linux Mint Debian Edition is built on the Debian Testing branch of code. It seems logical, to me, to expect LMDE to have the same Linux kernel that Debian Testing has. According to a Debian webpage Debian Testing presently has Linux kernel 3.16 series. 

There should be little or no visual differences between Linux Mint built on Debian and Linux Mint built on Ubuntu as it is the intention of the Linux Mint developers that there be no differences.

Debian developers release a new version of Debian whenever they decide the newer version is ready for release and not according to some release schedule. This is why Linux Mint Debian Edition has to be built on the Debian Testing branch of code. Otherwise, LMDE would fall behind Linux Mint built on Ubuntu.

Ubuntu developers have a six month release schedule with each new release having the latest stable Linux kernels. Linux Mint built on Ubuntu follows a similar release schedule with new Linux Mint releases coming one month after the Ubuntu release it is built on. This is how Linux Mint built on Ubuntu keeps up to date with the Linux kernels in Ubuntu.

The newer Linux kernels in the latest Ubuntu release are back-ported every six months into the Ubuntu Long Term Support (LTS) releases. This back-porting also includes the latest Linux firmware release. And it continues until the next Ubuntu LTS is released. This is how the Ubuntu developers keep their LTS releases up to date with the latest stable developments in Linux kernels and firmware.

The development branch of the next version of Ubuntu (15.05) is already using kernel 3.18 and may get kernel 3.19 by the time Ubuntu 15.04 is released. Only time will tell. To get the Linux kernel 3.18 in Debian a person would have to be running Debian Experimental.

It seems to me, that over time things even out. Debian Testing is a rolling release but there is a reason why it is called "Testing." Similarly there is a reason why the development branch of the next Ubuntu release is called the "Development Release." Things break. We expect that. Actually, things can be very stable. So, stable as to be boring. But Debian Testing and LMDE built on it and the Ubuntu Development release are places where the code can be tested.

As, I said earlier, this information is based upon just a little internet research. I know a little something about Ubuntu but little or nothing about Debian and next to nothing about Linux Mint. 

Regards.

---

### Post by kerry_s on 2015-01-28
i use debian testing, no issues. installed jessie using the net installer, then changed "jessie" to say "testing".

---

### Post by raptir on 2015-01-28
**LMDE** is based on Debian Testing but it pulls its packages as "Update Packs" so it does not always have the most up-to-date packages. You *can* change your sources to track Debian Testing directly but it can cause some dependency issues since there are Linux Mint repos that have their own packages. LMDE is distributed as a live CD and is as easy to install as Linux Mint or Ubuntu.

Keep in mind that ***LMDE will soon be based on Debian Stable.*** It is not going to follow the rolling release model they had initially planned but will instead be a set release that follows Stable.

**Debian** is distributed as either the Stable version (currently Wheezy, 7.8) and the Testing version (currently Jessie, 8.0). Jessie should become Stable sometime in the near future, but there are no hard release dates. There are live CDs available for Wheezy but the default install method is to run the Debian Installer from a CD/flash drive and install from there. You can choose which desktop environment you want to install during the install process. It is not significantly harder to install than Linux Mint but you do need to be a little more familiar with the process.

You can setup your sources to track testing instead of jessie. This will keep you up to date after Jessie is released and there is a new release in Testing. It's not a true "rolling distribution" since there is a package freeze that occurs, but it will keep you more up to date than Stable.

---

