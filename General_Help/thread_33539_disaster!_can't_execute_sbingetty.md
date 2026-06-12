---
title: "disaster! can't execute /sbin/getty"
date: 2005-05-11
forum: General Help
---

### Post by 23meg on 2005-05-11
i'm struck by a disaster. i can't boot Hoary at all, with neither the 686 nor the 386 kernels, also no luck in recovery modes. 

last thing i can see in the regular boot procedure before error messages flood the screen is "Creating initial device nodes". in the tail of the messages i can see "cannot execute /sbin/getty" and "Id 1 respawning too fast" ,"Id 2 respawning too fast".. etc.

last modifications i made before rebooting: set read/write access on a fat32 partition, modified fstab to mount this partition on startup.

 ](*,)  H E L P ! ! !   ](*,)

---

### Post by 23meg on 2005-05-11
update: when i try to access my linux partitions via windows using paragon mount everything (which is an app for mounting ext2/ext3 partitions under windows) i get a "crosslinked partitions!" error at startup, and it doesn't recognize any of the ext3 partitions; it displays the whole space occupied by them as "invalid".

update 2: when i launched partition magic in windows it detected about a dozen partition table errors and offered to correct them. i let it do its job and now it sees my whole hd as "BAD" (means corrupt in partition magicish). i'm typing this in the wonderful [slax](http://www.slax.org) live cd distro, which pleasantly surprised me by mounting my /home partition (not the root, swap, tmp but home, where most of my non-backed up cruical data is!), so i'll probably be able to rescue my data, but i want to spare myself the hassle of reinstalling Hoary...

---

### Post by 23meg on 2005-05-12
fixed this. slax didn't give me the privileges to write files to the ubuntu home partition, and didn't allow me to set them, so i tried the with the mepis live cd, and that worked. i copied my backed up fstab over the modified one and ubuntu booted as usual. i'm glad to be back in hoary world after having to put up with a few hours of slack and kde ;)

---

