---
title: "Problem &quot;unknown&quot; partition on HDD"
date: 2015-08-24
forum: General Help
---

### Post by t0p on 2015-08-24
I was doing some Gparted stuff and saw this:
[IMG]https://dl.dropboxusercontent.com/u/3409386/dev-sda-prob-gparted.png[/IMG]

You see /dev/sda6 has an exclamation mark, unknown file system... and it's 5.85 GB so it's not just chickenfeed.

Any ideas how I can find out what's on it/what it's for/can I make it useful if it's not already useful.  

Also there are a couple of unallocated partitions (I guess) called "unallocated".  Any ideas?

Thanks!

---

### Post by oldos2er on 2015-08-24
Right-click on sda6, and see if "Information" tells you anything useful.

"Unallocated" aren't partitions, just unused disk space. Nothing really to be concerned about.

---

### Post by westie457 on 2015-08-24
Could sda6 be a badly formed swap partition?

If so in Gparted right-click > format to > linux-swap.

After that edit fstab to add to the system. Unfortunately I am not proficient enough to explain the procedure.

---

