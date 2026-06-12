---
title: "Can't configure syslinux to show a menu for multiple options"
date: 2013-02-25
forum: General Help
---

### Post by Pocc on 2013-02-25
Hi all,

I have Ubuntu 12.04.02 LTS on an ADATA S102 16GB USB 3.0. I noticed that it boots much faster when persistence isn't enabled. I wanted to be able to use two different options, one with and without the persistence partition.

Partitions:
2GB for OS
13.4 GB casper-rw

This is my syslinux.cfg currently: 

*****

default menu.c32
prompt 0
menu title My Distro Installer

timeout 600
f1 help.txt
f2 version.txt

# D-I config version 2.0
	include menu.cfg
	default vesamenu.c32
	prompt 0
	timeout 50	
	ui gfxboot bootlogo

default persistent
  say Booting a persistent Ubuntu session...
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --

*****

I tried to make a menu with the first 2 paragraphs. The 3rd and 4th boot non-persistence and persistence respectively. When I try to boot with the current syslinux.cfg, it says that there is a missing operating system.

I'm looking for both suggestions and pointers to how to read syslinux.cfg files. Thanks!

---

### Post by Pocc on 2013-03-01
Advice for further research?

---

