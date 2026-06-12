---
title: "Inner workings of the ubuntu livecd"
date: 2008-03-14
forum: General Help
---

### Post by Nzer24 on 2008-03-14
I'm thinking about making a livecd distro that is able to load parts of it's filesystem modularly so that it can adapt to a specific task. I already understand how the squashfs and initrd systems work on a livecd, but one thing about the ubuntu cd puzzles me. If I am chrooted to the squashfs filesystem on the cd, and I install a package from apt, how does it integrate into the read-only filesystem? I know it's stored in memory, but why can many files integrate without the need for hundreds of mounted ramdisks?

I've seen that the Gentoo minimal cds can't do this (although they don't have a package manager installed), so why can ubuntu?

---

### Post by Nzer24 on 2008-03-14
Surely someone knows how that works. Please answer if you can...

---

### Post by Nzer24 on 2008-03-14
Well, I figured it out anyway. It's a merging of the squashfs and tmpfs filesystems via unionfs. This makes all writes go to the tmpfs, which has greater priority than the squashfs (and is writeable). Now I'm going to try and implement that with a series of squashfs files under unionfs, along with an optional ramdisk for write ability.

Consider this solved.

---

