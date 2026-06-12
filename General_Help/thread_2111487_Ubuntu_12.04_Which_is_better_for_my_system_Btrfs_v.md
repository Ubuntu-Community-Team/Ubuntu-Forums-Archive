---
title: "Ubuntu 12.04:: Which is better for my system? Btrfs vs Ext4"
date: 2013-02-02
forum: General Help
---

### Post by jomoyomo on 2013-02-02
/ mounted at SSD, 20GB
/home mounted at HDD, 200GB
RAM : DDR3 1600MHz 4GB*2
swap: HDD, 4GB
 
Which Settings do you recomment at installing ubuntu12.04?
btrfs vs ext4?on Which partition?
For me, stability and less battery consumption is much important:)

---

### Post by Impavidus on 2013-02-02
I don't know how current this information is, but to quote wikipedia:> **Btrfs** (**B-tree file system**, variously pronounced "*Butter F S*", "*Butterfuss*", "*Better F S*",[[4]]("http://en.wikipedia.org/wiki/Btrfs#cite_note-CM090622-4") or "*B-tree F S*"[[5]]("http://en.wikipedia.org/wiki/Btrfs#cite_note-5")) is a [GPL]("http://en.wikipedia.org/wiki/GNU_General_Public_License")-licensed experimental [copy-on-write]("http://en.wikipedia.org/wiki/Copy-on-write") [file system]("http://en.wikipedia.org/wiki/File_system") for [Linux]("http://en.wikipedia.org/wiki/Linux"). Development began at [Oracle Corporation]("http://en.wikipedia.org/wiki/Oracle_Corporation")  in 2007. **[COLOR=Red]It is still in heavy development and marked as unstable.[/COLOR]**  Especially when the filesystem becomes full, no-space conditions arise  which might make it challenging to delete files.I would use ext4 if you want stability.

As for battery consumption, there are several tricks that can save you a few percent each: dimming the screen, switching off wireless technology when you do't need it, spinning down hard drives, trottling the CPU, reducing the network bitrate, switching off the graphics card if you also have lower performance on-board graphics, et cetera.

---

### Post by Yellow Pasque on 2013-02-02
Use ext4, unless you need a btrfs feature that ext4 lacks (and if you have to ask, you probably don't).

---

### Post by tgalati4 on 2013-02-02
Live on the edge and try btrfs.  If it works for you, great.  If it breaks, you get to keep the pieces.

Neither one will affect power consumption.

---

