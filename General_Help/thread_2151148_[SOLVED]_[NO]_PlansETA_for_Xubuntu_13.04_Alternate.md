---
title: "[SOLVED] [NO] Plans/ETA for Xubuntu 13.04 Alternate ISO?"
date: 2013-06-03
forum: General Help
---

### Post by GeneralShenanigans on 2013-06-03
We are currently utilizing preseed and postinstall functionality for an automated USB stick installer of Xubuntu 12.04.2, and would like to upgrade to 13.04 (via fresh install; we'd like to avoid do-release-upgrade).

From what I've been told, the preseed/postinstall functionality only works for alternate installer ISOs. I've been checking weekly since 13.04 was released for an xubuntu-13.04-alternate-amd64.iso release, but I've yet to find one. 

Are there plans to release it? If not, I suppose I could use a Ubuntu alternate ISO and manually remove gnome and install XFCE, but I'd like to avoid that if possible.

Thanks!

---

### Post by plucky on 2013-06-03
> **GeneralShenanigans said:**
> We are currently utilizing preseed and postinstall functionality for an automated USB stick installer of Xubuntu 12.04.2, and would like to upgrade to 13.04 (via fresh install; we'd like to avoid do-release-upgrade).

From what I've been told, the preseed/postinstall functionality only works for alternate installer ISOs. I've been checking weekly since 13.04 was released for an xubuntu-13.04-alternate-amd64.iso release, but I've yet to find one. 

Are there plans to release it? If not, I suppose I could use a Ubuntu alternate ISO and manually remove gnome and install XFCE, but I'd like to avoid that if possible.

Thanks!

Support for the Alternate install CD was dropped in Quantal release.

From Quantal Release Notes > New Features in Ubuntu

There is no longer a traditional CD-sized image, DVD or alternate image, but rather a single 800MB Ubuntu image that can be used from USB or DVD. Users who previously installed using LVM or full-disk encryption via the alternate CD will find that these installation targets are supported by the consolidated image in 12.10. 

Good Luck

---

### Post by ajgreeny on 2013-06-03
You could, as an alternative, get the minimum install CD .iso file and use that to install your system, choosing **xubuntu-desktop** as the package install choice and you will end up with exactly the same OS as a normally installed Xubuntu 13.04.

I have done it for another of the *ubuntu family a year or two ago and it all went without a hitch; it just makes the installation job a bit slow in comparison to a normal one, simply because all the packages normally downloaded in the .iso file have to be downloaded as the installation occurs.  It does mean, however, that having downloaded as you installed, there will be no immediate updates to apply, which can take quite a while after a normal installation with perhaps 100 -200 packages that are out of date a few months after release.

I am not sure if your intended way of updating/installing will be possible using the mini .iso, but just throw out the idea as something to look into.

---

### Post by GeneralShenanigans on 2013-06-03
> **ajgreeny said:**
> You could, as an alternative, get the minimum install CD .iso file and use that to install your system, choosing **xubuntu-desktop** as the package install choice and you will end up with exactly the same OS as a normally installed Xubuntu 13.04.

I have done it for another of the *ubuntu family a year or two ago and it all went without a hitch; it just makes the installation job a bit slow in comparison to a normal one, simply because all the packages normally downloaded in the .iso file have to be downloaded as the installation occurs.  It does mean, however, that having downloaded as you installed, there will be no immediate updates to apply, which can take quite a while after a normal installation with perhaps 100 -200 packages that are out of date a few months after release.

I am not sure if your intended way of updating/installing will be possible using the mini .iso, but just throw out the idea as something to look into.

Good call, I wasn't aware that a mini ISO existed.

Our computers are on painfully slow internet connections (single T1s), so what we do is keep a copy of all the necessary debs on the USB installer, and the first action of the postinstall script is to copy all the debs from there to /var/cache/apt/archives to minimize downloading of debs. Then at the end of the installer, we do the reverse: copy all downloaded debs back to the USB drive, so that they're not downloaded the next time it's used.

I just prepped a USB drive with our current preseed/postinstall and the 13.04 mini ISO. I will let you know how it goes.

Thanks!!

---

### Post by Cheesehead on 2013-06-03
> **GeneralShenanigans said:**
> From what I've been told, the preseed/postinstall functionality only works for alternate installer ISOs.

You have been misinformed. All Ubuntu installers use the preseed file, if one is found.

---

### Post by GeneralShenanigans on 2013-06-03
Good to know! We ought to be using the minimal ISO anyways... 

I'm currently working on the learning curve of syslinux and preseeding... I should be able to make this work. Marking topic as closed.

Thanks everyone!

---

