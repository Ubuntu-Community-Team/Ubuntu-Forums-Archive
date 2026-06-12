---
title: "Resizing / partition (ext3) with gparted"
date: 2006-11-20
forum: General Help
---

### Post by mtpadilla on 2006-11-20
Hi. I'm a relatively new Ubuntu user and realize that the space I originally allocated to the / partition (my root Ubuntu linux partition) is way too large than necessary and I'd like to reclaim the unused space to store music.

I've looked on the forums and apparently gparted is a good tool. I've used it from within Edgy (not using a gparted live cd) and it shows little locks next to each of my partitions, apparently meaning that I can't change them. Hmmm...

Some questions:
- Is this (using gparted within Edgy, not using the gparted live cd) the best way to go about this?

- Will resizing the partition and creating a new ext3 partition with the freed up space screw up the data currently on the partition I wish to resize?

- How can I get around these locked partitions?

Here is what I'm seeing w/ gparted:
[http://www.stanford.edu/~mtp/temp/Screenshot-1.png]("http://www.stanford.edu/~mtp/temp/Screenshot-1.png")

Any comments/suggestions would be super. Thank you very much in advance!!

---

### Post by meng on 2006-11-20
You can't (or at least shouldn't) resize partitions while you're actually using them. My advice is to download and burn the GParted LiveCD, boot from it, so that your hard drive partitions are not being used, and then resize/move to your heart's content.

---

