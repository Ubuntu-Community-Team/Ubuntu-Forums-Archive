---
title: "Running Ubuntu alongside Gentoo"
date: 2018-07-23
forum: General Help
---

### Post by Crafty Kisses on 2018-07-23
Since I don't have time to do a thorough install, and rushing a Gentoo install always leaves regrets somewhere, I would like a tried and tested means to pick away at a Gentoo configuration on a live Ubuntu machine. Ultimately, I'd like to be able to boot into a Gentoo environment complete enough to use it as the production OS. 

Booting live media is not an option as I need the uptime on the server. The options I am considering: 

[LIST]
[*]I use btrfs and think unpacking a stage3 into a subvolume would work, but my /boot is on a vfat partition for UEFI, which would leave me using the Canonical kernel. 
[*]My next thought was to mount some free disk space and install there, but my extra disk partition is on an HDD, and I'l like the install to live on my SSD (which Ubuntu currently occupies). 
[*]LXC might be an option if I bind mount something, install to it, then tar the fs and unpack it over Ubuntu. 
[/LIST]
Same idea with KVM or Vbox -- install, rsync/tar, then wipe Ubuntu and unpack. So, I have options, but before I start this has anyone done something similar with solid results, so I could run Ubuntu/Gentoo along side each other?

---

