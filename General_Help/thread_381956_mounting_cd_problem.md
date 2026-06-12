---
title: "mounting cd problem"
date: 2007-03-11
forum: General Help
---

### Post by Patrick Urs on 2007-03-11
First: Hello, Im new here. I started using ubuntu a couple of months ago, and found it do be the best distro I tried. Anyway, I'm currently having a problem:


One day, after I installed wine, I thought it might be fun to see if itunes (normally I use banshee with my ipod) would install. So I popped in the ipod cd and ran the installer with wine. It worked fine until it quit because of some quicktime thing. I didn't really mind, and went back to banshee. I noticed that although the cd was still in the drive, It wasn't on the desktop anymore. I ignored it, and rebooted. The cd still didn't show up. I tried another cd, this time an audio cd. Nothing. I openend sound juicer and it showed that the cd drive was still there, but no disk. Banshee didn't display anything.


So, basically, how do I fix this? :confused: 

Thanks in advance.

---

### Post by dcstar on 2007-03-11
> **Patrick Urs said:**
> First: Hello, Im new here. I started using ubuntu a couple of months ago, and found it do be the best distro I tried. Anyway, I'm currently having a problem:


One day, after I installed wine, I thought it might be fun to see if itunes (normally I use banshee with my ipod) would install. So I popped in the ipod cd and ran the installer with wine. It worked fine until it quit because of some quicktime thing. I didn't really mind, and went back to banshee. I noticed that although the cd was still in the drive, It wasn't on the desktop anymore. I ignored it, and rebooted. The cd still didn't show up. I tried another cd, this time an audio cd. Nothing. I openend sound juicer and it showed that the cd drive was still there, but no disk. Banshee didn't display anything.


So, basically, how do I fix this? :confused: 

Thanks in advance.

Check **System-Preferences-Removable Drives and Media** and verify that the correct boxes are ticked to do what you want.

---

### Post by Patrick Urs on 2007-03-11
I already checked that. Everything will do what it's supposed to. Is there a way I could mount it manually? I tried, but nothing came of it.

---

### Post by themaceisback on 2008-01-17
> **Patrick Urs said:**
> I already checked that. Everything will do what it's supposed to. Is there a way I could mount it manually? I tried, but nothing came of it.

in the terminal type (mount /dev/cdrom /mnt/)

with out the ()

---

