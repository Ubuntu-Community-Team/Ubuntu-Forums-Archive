---
title: "GRUB question"
date: 2007-07-16
forum: General Help
---

### Post by EasyWind on 2007-07-16
Hi all...

I am VERY new to Linux and Ubuntu and have some questions about getting started...

First, I have installed Ubuntu 6.1 from CD and am setting it up as a  dual boot with Windows XP Pro SP2.

I used Partition Magic to set up the hard drive for the dual boot and was planning on using Boot Magic for the BM but from what I have been able to find online, that might not have been the best choice as I am unable to start Ubuntu at login although it does show up as one of the possible selections.

I found Super GRUB and further reading suggests this might be a better choice for the BM.

The questions I have are will  Super GRUB "fix" the boot manager issues on the fly or do I need to uninstall Ubuntu and then run the GRUB program followed by a reinstall of Ubuntu?

I am kinda uncomfortable with the whole command line thing but I am not afraid to learn - it would be nice if I could at least get the dual boot thing running right...

---

### Post by dreadlord_chris on 2007-07-16
I'm confused - why are you making this so hard on yourself? Just follow these directions:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

There is really no reason to use a 3rd party boot manager for a simple XP/Ubuntu dual-boot

---

### Post by loserboy on 2007-07-16
yea, installing Ubuntu will automatically install GRUB, and in turn it will detect your XP install..... no reason at all for a 3rd party program.
now I'm not posititve but with the info that you've given I think you should just re-install Ubuntu over the old ubuntu and let GRUB write itself to the default location, then everything should be fine

---

