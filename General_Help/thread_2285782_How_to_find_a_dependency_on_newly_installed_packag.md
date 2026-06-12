---
title: "How to find a dependency on newly installed packages ?"
date: 2015-07-08
forum: General Help
---

### Post by georgesgiralt on 2015-07-08
Hello !
I've a Lenovo Thinkpad. It is a GPT partitioned system with an EFI boot system. I installed Ubuntu 14.04.2 LTS on it.
So I've got the EFI-Grub packages installed, 
As I wanted to get all the Thinkpad idiosyncrasies solved, using Synaptics I installed the following package list : 
```

acpi-call-dkms (1.1.0-2)
acpitool (0.5.1-3)
libdw1 (0.158-0ubuntu5.2)
libunwind8 (1.1-2.2ubuntu3)
libxosd2 (2.2.14-2.1)
linux-lts-vivid-tools-3.19.0-22 (3.19.0-22.22~14.04.1)
linux-tools-3.19.0-22-generic (3.19.0-22.22~14.04.1)
linux-tools-common (3.13.0-57.95)
linux-tools-virtual-lts-vivid (3.19.0.22.9)
thinkfan (0.8.1-1)
tlp (0.7-2~trusty)
tlp-rdw (0.7-2~trusty)
tp-smapi-dkms (0.41-1)
tpacpi-bat (2.1-0ubuntu0morgwai1)
tpb (0.6.4-8

```

And now, when I try to update my system, apt-get wants to remove the Grub-Efi packages and install the plain grub one instead. 
So I would like to find the newly installed package requiring the plain GRUB in order to remove it (and complaining about this, btw...) 
Many many many thanks for your help and answer ! 
Have a nice day.

---

### Post by Bucky Ball on 2015-07-08
Erm, where did you get the list to install all that and were you having 'Thinkpad problems' and that is why you installed it? You are dragging in stuff from Vivid there for 14.04.1 and you are running .2. :-k

If you want to find dependencies, find the software in Synaptics and right click> Properties.

---

### Post by georgesgiralt on 2015-07-08
So I followed your advice and looked at each package properties. None was claiming a dependency on Grub ! 
So I re ran apt-get update and apt-get upgrade and, guess what, it showed a new Grub-EFi package and did not ask for removal of the grub-efi anymore... Maybe I had a broken package which was updated during the time we questioned each other .. 
Thank you anyway for the help and advice, I learned a new trick ! 
Have a nice day.

---

