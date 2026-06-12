---
title: "[SOLVED] ntfs installation..."
date: 2008-01-07
forum: General Help
---

### Post by buccaneere on 2008-01-07
[HTML]chucknb@chucknb-desktop:~$ sudo apt-get install ntfs-3g
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/HTML]

What's this mean?

I live in a brick home, and I put my Christmas tree is up early this year, if that makes a difference (ya' never know, with open source:lolflag:)

---

### Post by vanadium on 2008-01-07
If looks like you still had synaptic open when issuing the apt-get command at the prompt. Only one "installation" program (synaptic, aptitude, or apt-get) may be active: other instances are locked out. Thus, make sure you have Synaptic (or update manager) closed before trying to use apt-get.

---

### Post by forestpixie on 2008-01-07
it usually means that a bit of the tree has got into the wall - you'll need a builder or a tree surgeon

the other menaing is quite often that you have add/remove or synaptic open - or maybe the update manager is working while you try to apt-get

---

### Post by buccaneere on 2008-01-07
Thanks there...

So since I jammed up the install, do I need to re-install?

---

### Post by stump138 on 2008-01-07
It never installed, so you'll have to try it again :)

---

### Post by buccaneere on 2008-01-07
[HTML]chucknb@chucknb-desktop:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
The following packages were automatically installed and are no longer required:
  libraw1394-5 libdbus-1-2 vlc-plugin-alsa wxvlc librpcsecgss3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/HTML]

Now what?

My ntfs-formatted drive ain't mappin, or showin' up at 'mount'. It is showin' properly as slave on IDE secondary in BIOS.

Help?

---

### Post by bodhi.zazen on 2008-01-07
Try ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by vanadium on 2008-01-08
Now, you are now reporting a different problem than the one for which you started this thread. My assumption is that your ntfs file system needs to be checked because it is "unclean". Ubuntu won mount automatically unclean volumes, though you can still manually mount with the force option at your own risk.

---

### Post by buccaneere on 2008-01-08
> **bodhi.zazen said:**
> Try ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

Hi bodiz...

It is mapped now.

I think the upgrade to FF last night got necessary drivers in.

---

