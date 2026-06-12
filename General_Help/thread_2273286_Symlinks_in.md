---
title: "Symlinks in /"
date: 2015-04-11
forum: General Help
---

### Post by GQDQALC on 2015-04-11
Hi,

I have my OS installed in one partition but most of my data in another, which I mount. I want my installed programs to be available if I ever need to i.e. switch between versions of Ubuntu. Can I copy the directories in / (i.e. bin, usr, opt) to my other (mounted) partition and just leave symlinks in /? If I can with some but not all, which can I do it in?

---

### Post by dino99 on 2015-04-12
you does not need to tweak  as such, the system deal it for you; otherwise be ready to fight against huge issues

---

### Post by Impavidus on 2015-04-12
No. Programs have been compiled to run on a specific version version of Ubuntu, with specific libraries. Merging directories with executables and libraries requires a huge amount of manual tweaking and the package manager would work anymore. Furthermore, /bin has to be on the root partition. Even mounting it there won't work, let alone symlinking it. This is because /bin contains the code necessary to mount a partition.

You can however create a list of installed packages and synchronise that between two Ubuntu systems, which will give both version the same software installed. To generate a list on one Ubuntu, run```
dpkg --get-selections > package.txt
```which will save a list of packages in the file package.txt. On the other Ubuntu, possibly a different version, you can run```
sudo dpkg --set-selections < package.txt
sudo apt-get dselect-upgrade
```to install all packages that were installed on the previous system. Note however that some packages may no longer be available and all packages will be marked as manually installed, so autoremove won't work very well.

---

### Post by GQDQALC on 2015-04-12
Part of the reason is that I want to save space on my OS partition, which is getting full. Can I keep core system files on my OS partition but move my installations (and default install location) to a different one?

---

### Post by dino99 on 2015-04-12
to do some room you have several ways:
- uninstall apps you does not need (what a genius idea :p): purge the meta-packages: 'ubuntu-desktop', '  xserver-xorg-input-all', xserver-xorg-video-all' then purge all the related packages you does not need.
- install localepurge to delete all the 'exotic' languages you does not care about, idem for the printers you does not have
- purge the DE you does not use (either unity/gnome-shell/...) and games, ...
- clean your system: clean/autoclean/autoremove
- purge the orphans with gtkorphan
- set your swap partition to a minimum, then resize the other partitions (when they are not mounted indeed)
- use a /home partition on an other device (or move your data only, as you wish)

.... the limit is your brain, but take care of the mandatory dependencies (synaptic will help you to avoid errors)

---

### Post by Impavidus on 2015-04-12
I'm not entirely sure what you mean...

It is possible to move some directories to a different partition. Partitions only containing data files (no user config files, no files installed via the package manager) can be shared between multiple OSs.

But how large is your OS partition and how full is it? Cleaning and purging everything you don't need may give you a few gigabytes.

---

