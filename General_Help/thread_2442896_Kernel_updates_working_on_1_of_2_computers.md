---
title: "Kernel updates working on 1 of 2 computers"
date: 2020-05-08
forum: General Help
---

### Post by mcellius on 2020-05-08
I'm running two fresh installs of Ubuntu 20.04, one on a Dell desktop and the other on a System76 laptop.  I run updates every day on both: however, although the kernel has been updated several times on the desktop computer, it has not been updated on the laptop, so that the two are now running different versions of the kernel.  As of now, they are running these versions:

laptop: 5.4.0-28-generic
desktop: 5.4.0-30-generic

All other updates appear to identical, both to the system and to installed programs.

The update script I run every day on each computer has these commands, and only these:

```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
```

Both computers are running very well with Ubuntu 20.04 and have no errors or any other problems.  Honestly, if I didn't have two computers so I notice the difference, I'd never think for a second that something wasn't quite right.

So why is the kernel being updated on one and not the other?  Any ideas/suggestions?

---

### Post by dino99 on 2020-05-09
i suppose your laptop has not the 'proposed' archive enabled; check it via synaptic for example

---

### Post by mcellius on 2020-05-09
Thanks.  However, I just checked that and it isn't it: it's enabled on both computers.

---

### Post by Impavidus on 2020-05-09
I typically keep the proposed repo disabled unless I really need it for a quick bugfix.

Maybe the metapackage drawing in the kernel upgrades is missing on one of the computers. With the standard kernel, it's called linux-image-generic.

---

### Post by mcellius on 2020-05-09
Yeah, I don't usually keep the proposed repository enabled, either.  After the fresh installations, though, I figured there might be new things coming down soon and I wanted to see how it'd go.  After a couple more weeks I'll probably turn it off.

As to the metapackage in kernal upgrades, I know nothing about that.  I wouldn't know how I would go about fixing that.  Should I even try, or maybe just go ahead and reinstall?

---

### Post by Impavidus on 2020-05-10
When a kernel upgrade is issued, a new version of the metapackage is released. The package manager will then try to upgrade the metapackage. The new version of the metapackage has a new dependency, which is the package containing the new kernel, and the package manager installs that too. This way kernel upgrades can be automatically installed without automatically removing the previous kernel at the same time.

If the metapackage is missing, it should be very easy to fix. Have a look at the currently installed packages:```
dpkg --list | grep linux-
```It should show an interesting difference between your two computers.

---

