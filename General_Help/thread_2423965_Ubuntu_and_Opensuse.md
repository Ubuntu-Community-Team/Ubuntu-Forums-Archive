---
title: "Ubuntu and Opensuse"
date: 2019-08-01
forum: General Help
---

### Post by john19502 on 2019-08-01
I have Ubuntu 19.04, 19.10, Linux Mint, Windows and Opensuse on my PC. When any of the flavors of Ubuntu update the grub I lose access to opensuse and have to upgrade opensuse from my boot disk to get it back. Ubuntu does not find opensuse but opensuse finds Ubuntu.

---

### Post by speartip on 2019-08-01
That sometimes happens. I have the same problem with Ubuntu & Manjaro. Best thing to do is have opensuse control Grub, Then lock grub on Mint & Ubuntu. You can do this by searching for Grub in Synaptic. Highlight the Grub packages, which are probably, grub-common, grub-pc, grub-pc-bin & grub2-common. Then click "package" & "lock-version". This will stop them updating along with the regular upgrades.

---

### Post by HermanAB on 2019-08-01
Hmm, dual booting is so 20th century.  Install Gnome Boxes, make virtual machines and then you can run all of them at the same time if you want.

---

### Post by oldfred on 2019-08-01
Is OpenSuse using LVM?
       sudo apt-get install lvm2 

Other installs may need you to install correct drivers to support the other install or mount other install's partitions/volumes so it can be seen.

---

