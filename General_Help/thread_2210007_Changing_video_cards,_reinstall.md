---
title: "Changing video cards, reinstall?"
date: 2014-03-08
forum: General Help
---

### Post by javajeff1 on 2014-03-08
I was curious if most of you would reinstall an OS when changing from an ATI to nvidia video card.  My new card is arriving this week.  :)

---

### Post by howefield on 2014-03-08
I wouldn't necessarily reinstall the OS, but I would uninstall any proprietary drivers before making the hardware change :)

---

### Post by javajeff1 on 2014-03-08
yeah.  I am only using the ATI open source drivers atm.  Are there any issues switching brands?  I would like to be able to install the nvidia proprietary drivers after I put the new card in.  I usually do a fresh install with each release anyways.

I have been uninstalling ATI drivers like this:
$ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

---

### Post by david98 on 2014-03-08
If you usually install a fresh OS with every new release I would just wait for the new 14.04 release and install it with your new hardware. Or even try it with your new hardware once the proprietary drivers where removed. Or just do a fresh install of 13.10 then install drivers and do a upgrade once 14.04 has been released as a lts.

---

### Post by javajeff1 on 2014-03-08
Thanks for the response.  I have separate /home, OS, and swap partitions and always do custom installs.  I have tried upgrades in the past and had some issues.  I do not know if these newer versions upgrade smoother.  What are your experiences on going the upgrade route?  I generally install a handful of programs from downloaded sources, and everything else from the software center.

---

### Post by david98 on 2014-03-08
I do a upgrade on every version yes  it's a cleaner install to do afresh but in general I have not had any problems since 12.10 but I have always got a clone of my hdd using clonezilla and backup daily using deja. Since you have your download sources to hand I would think you should not have any problems with an upgrade as am sure you know your files are saved so you can easily cut and paste your download sources and install your preferred programs as you would usually. But no matter what you do as any body on the forum would recommend is to back your important data up regularly and if possible back it up twice because you never know.

---

### Post by papibe on 2014-03-08
Hi javajeff1.

In case it exists, I'd also remove (or rename) the X configuration file:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.ati.old
```
Regards.

---

### Post by javajeff1 on 2014-03-08
> **david98 said:**
> But no matter what you do as any body on the forum would recommend is to back your important data up regularly and if possible back it up twice because you never know.

Of course.  I keep important stuff on multiple hard drives.  I also use Truecrypt, which happens to be one of my installs by download from their site.

---

