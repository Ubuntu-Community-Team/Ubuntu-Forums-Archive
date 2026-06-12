---
title: "How hard is it to install LVM?"
date: 2007-04-19
forum: General Help
---

### Post by groggyboy on 2007-04-19
I've been using Feisty since about Herd 4, and with the final release coming out today, I've decided a fresh install may be in order (to get rid of any lingering kinks in the system).

With this fresh install, i've decided to convert my root and home partitions from ext3 to XFS, because I've read a handful of articles ([like this one]("http://www.debian-administration.org/articles/388")) that have high praise for this filesystem.

in addition, i'm curious about LVM (partly because of [this blog]("http://xlntsolution.blogspot.com/2007/03/feisty-performance-fly-like-butterfly.html")).  I've read through a bit of the [LVM HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO/index.html") as well.

My current setup is something like this (all primary partitions):
      >  /dev/sda1 - 9 GB - Ubuntu /root
      >  /dev/sda2 - 9 GB - PCLinuxOS /root (or the linux flavour of the day)
      >  /dev/sda3 - 41 GB - /home & storage
      >  /dev/sda4 - 1 GB - swap

But before i jump in head first and set up LVM, i have a few questions:
1. Considering I have only one hard drive, would LVM be worthwhile?
2. Does LVM work across multiple linux installations?  Could my Ubuntu and PCLOS root directories share a logical volume?
3. Should I place my storage directory in a separate logical volume from the root directories (and should i split storage and and home into three parts - PCLOS /home, ubuntu /home, and /storage)?
4. This is the important question.  How hard is it to set up an LVM system?  I have a good grasp of linux, but the [LVM HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO/index.html") is still rather daunting.  Anyone know of any easier howto's?

cheers!
groggyboy

---

