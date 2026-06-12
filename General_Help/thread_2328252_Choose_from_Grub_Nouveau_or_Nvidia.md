---
title: "Choose from Grub Nouveau or Nvidia"
date: 2016-06-19
forum: General Help
---

### Post by gpaunescu2 on 2016-06-19
Hi,

I have a laptop MSI GS60 6QE; CPU is Skylake I7-6700HQ and GPU NVIDIA GTX 970.
I had installed Ubuntu 16.04 on it and is working quiet good.
I've installed NVIDIA 364.19 from [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)
I'm using Prime to select the graphic card.
I noticed that when I using this configuration, over the nouveau driver, the battery life is very short (about 1h 30mins)
If I using nouveau the battery life is better (about 2:30 to 3 h).
My question is  that if I can configure Ubuntu to choose at boot time, from Grub, which driver to use NVIDIA or nouveau?
I've searching on internet and I found something similar, but is for Fedora and I'm not so good to convert it 
to Ubuntu; also was for some older versions and as I saw, there are some changes in the latest version of Ubuntu.

Thank you in advance for any help.

Gabriel

---

### Post by DuckHook on 2016-06-20
Even if possible, this is a non-trivial change that would lead to a very brittle system. It's not simply a matter of choosing drivers: each driver installs its own libraries and configs which are incompatible with the other. This is why even the standard method of changing drivers will often lead to display problems unless the old driver is not just uninstalled but actually purged.

A better workaround for what you are trying to do might be to actually install a dual boot, both consisting of Ubuntu Xenial, but with the nouveau driver on one install and the nVidia on the other. You can create a third partition for /home and set both install instances to the same /home. You will have to update/upgrade twice, but this shouldn't be a big hardship. A bigger concern is the doubled HDD space, but a root partition of 30GB should do, and the shared /home will be efficient. GRUB will sense the other OS and offer you the choice of either at boot. You will have to edit GRUB descriptions to differentiate between the two.

---

### Post by gpaunescu2 on 2016-06-20
> **DuckHook said:**
> Even if possible, this is a non-trivial change that would lead to a very brittle system. It's not simply a matter of choosing drivers: each driver installs its own libraries and configs which are incompatible with the other. This is why even the standard method of changing drivers will often lead to display problems unless the old driver is not just uninstalled but actually purged.

A better workaround for what you are trying to do might be to actually install a dual boot, both consisting of Ubuntu Xenial, but with the nouveau driver on one install and the nVidia on the other. You can create a third partition for /home and set both install instances to the same /home. You will have to update/upgrade twice, but this shouldn't be a big hardship. A bigger concern is the doubled HDD space, but a root partition of 30GB should do, and the shared /home will be efficient. GRUB will sense the other OS and offer you the choice of either at boot. You will have to edit GRUB descriptions to differentiate between the two.

Hi,

Thanks for your answer. I know is not a trivial change.
I found here 
[http://www.funtoo.org/Create_a_boot_option_for_easy_nvidia_or_nouveau_display_driver_switching](http://www.funtoo.org/Create_a_boot_option_for_easy_nvidia_or_nouveau_display_driver_switching)
and here 
[https://wiki.gentoo.org/wiki/Nouveau_%26_nvidia-drivers_switching](https://wiki.gentoo.org/wiki/Nouveau_%26_nvidia-drivers_switching)

how to do for others distros. But I'm not very good to translate this for Ubuntu.
I not have another partition to install a duplicate Ubuntu.
Any way, I have installed both drivers on my machine; Nouveau is blacklisted to not be loaded.
Any test to make it works I will do first on external usb drive; I'm not very good to configure Ubuntu, but I'm able to make it works on my machine at the end.
I wish to try any solution.

Thanks again,
Gabriel

---

### Post by DuckHook on 2016-06-20
I came across those links too with a Google search. They all have various differences from Ubuntu, but the most relevant would be the gentoo link using systemd, as this is the same init system that Ubuntu now uses.

I am not qualified to help you with the details of such an implementation, so I hope a guru will notice this thread and jump in. However, I will alert you to the fact that any gentoo-based solution will be at a very high level and assumes you to be a Linux expert. I have a gentoo install in a virtual machine and it was by far the most complex install I have ever done, even compared to Arch. To be fair, the linked instructions are probably pretty easy for most Gentoo users because Gentoo requires users to build their own kernel as a matter of course.

You should also understand that custom-building your own kernel as per Gentoo instructions will mean that you can no longer rely on Ubuntu to auto-upgrade your OS for security updates, bug fixes, new features, etc. You are making a commitment to building each new kernel yourself. This is another reason why I recommended dual booting: it is by far the easiest solution for regular users, both to implement initially and to maintain afterwards.

---

