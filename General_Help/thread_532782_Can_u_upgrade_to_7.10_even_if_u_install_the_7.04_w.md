---
title: "Can u upgrade to 7.10 even if u install the 7.04 with WUBI???"
date: 2007-08-23
forum: General Help
---

### Post by sreejithr on 2007-08-23
i noe that u can reinstall it but can u do it without having to do that can u upgrade from ubuntu itself??

---

### Post by tuxcantfly on 2007-08-23
No; you'll probably have to reinstall; the Wubi-specific hacks are probably not going to work on Ubuntu 7.10. However, if you use LVPM (see my sig) to transfer your install to a dedicated partition, thus making it a "real" Ubuntu install, you should be able to use the upgrade manager to just upgrade to Ubuntu 7.10 once it's released.

---

### Post by sreejithr on 2007-08-24
is unebootin safe??? is it same as wubi or what is  the differnce...could u give me details on what it does??? u c my problem is that I tried installing ubuntu with a CD but i never managed to partition it....what does this do???

---

### Post by tuxcantfly on 2007-08-24
> is unebootin safe??? is it same as wubi or what is the differnce...could u give me details on what it does??? u c my problem is that I tried installing ubuntu with a CD but i never managed to partition it....what does this do???

It's different, as in Wubi installs to a loopmounted partition and UNetbootin installs to a real one, like the official Ubuntu does. It should be just about as safe, since the NTFS resizing code in Ubuntu has improved a lot and is now very reliable (though you might want to back up important data just in case). Essentially, it's identical to the standard installation process, only no CD is required; it downloads the installation files on the go from the internet while installing.

---

### Post by runemaste644 on 2007-09-08
I found there is a Linux headers upgrade. Would installing them mess up everything?

---

### Post by tuxcantfly on 2007-09-08
> **runemaste644 said:**
> I found there is a Linux headers upgrade. Would installing them mess up everything?

You don't need the linux-headers unless you're compiling kernel modules from source. Worst thing that would happen is that you'll lose the ability to compile kernel modules from souce if it doesn't work (so it should be safe to upgrade).

---

### Post by runemaste644 on 2007-09-09
Besides, all we need to know to answer this question once and for all is what happens when you do a dist-upgrade.
 Everything that happens.

---

### Post by tuxcantfly on 2007-09-09
> **runemaste644 said:**
> Besides, all we need to know to answer this question once and for all is what happens when you do a dist-upgrade.
 Everything that happens.

apt-get fetches the new deb packages for Gutsy from the repos, and installs them over the old ones. That's (technically) all, but since some system config files and boot procedures have changed since ubuntu 7.04, some things will almost surely break after a dist-upgrade

I wouldn't recommend dist-upgrading to Gutsy unless you're really familiar with system recovery; I'm practically sure something will break (unbootable system and the like). If you absolutely must try out Ubuntu 7.10, I'd just shrink your Windows partition, make a new partition for Ubuntu 7.10, and install it normally, not with Wubi; if you don't want to bother using a CD, just use UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) and select the Ubuntu 7.10 version, and it'll let you install Ubuntu 7.10 by downloading the installation files from the web.

---

