---
title: "Ubuntu 10.04: libxcb-sync0 &gt;= 1.6"
date: 2013-06-12
forum: General Help
---

### Post by TYPELiFE on 2013-06-12
How can I get this version of libxcb-sync0 installed? I see it available in xorg-edgers, however I added the PPA and the package isn't available to upgrade to.

Is it possible to update to this version via APT? If not, where can I get the source to build?

[https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1852267](https://launchpad.net/~xorg-edgers/+archive/ppa/+build/1852267)

Thanks!

---

### Post by Irihapeti on 2013-06-12
Ubuntu 10.04 has reached end-of-life and no more upgrades are available. This will apply not only to PPAs but all the packages.

It's best to upgrade your system. 12.04 is the next long-term support release and will be supported until 2017. If you don't like the idea of running Unity, there are plenty of other options available.

---

### Post by TYPELiFE on 2013-06-12
@Irihapeti

I'm definitely aware of that, however while trying to install 12.04 on my MacBook Air (2.1 - Mid 2009) I ran into a plethora of issues, so now that I have a working system put together, I wanted to avoid trying to upgrade for the time being.

I was able to resolve this issue myself, I found a repo being maintained for lucid that provides libxcb 1.6, anyone else in the same situation as me can find it at the link below. Once you've added the repo you can simply run: **sudo apt-get upgrade libxcb**

[https://launchpad.net/~kalon33/+archive/experimental-stuff](https://launchpad.net/~kalon33/+archive/experimental-stuff)

Cheers!

---

### Post by Dreamer Fithp Apprentice on 2013-06-12
> **TYPELiFE said:**
> 
I'm definitely aware of that, however while trying to install 12.04 on my MacBook Air (2.1 - Mid 2009) I ran into a plethora of issues, so now that I have a working system put together, I wanted to avoid trying to upgrade for the time being.
Can't say I blame you. 10.04 was certainly the most trouble free Ubuntu I've used. And I also had problems getting 12.04 to install but I eventually made it work. You might like to consider backing up your 10.04 system with Remastersys, which you install to the system you want to back up and run it from that system. It makes an iso which you can then burn and the resulting CD or DVD (or I suppose usb stick) is a live disk version of your tweaked installation which can also be used to REINSTALL that system to a hard drive. That way if you do try to upgrade or try some other distro you can easily restore what you know works if you want to. Also you've got a live disk you can boot some other machine from so you can use your own sysytem without installing anything. Or alternately, if you have another bootable partion on the machine you might like to back up the 10.04 with something like fsachiver while you are booted from the other partition. That's probably a little faster if you have no interest in a live disk.

---

