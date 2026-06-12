---
title: "[SOLVED] what's that partitioning command for the CLI?"
date: 2008-02-28
forum: General Help
---

### Post by bluepowder7 on 2008-02-28
hey all,

a few days ago, i used a command on 7.10 Server edition (so it's ALL command line) that gave me a nice "gui" for making and formatting partitions.  i can't find the page that talked about it in my firefox history, but what i can remember is this:

* it was a gui, like back in the DOS days, all text based and you used the arrow keys to move around
* it was able to partition and format into any file system, using the filesystem codes (like 8e for "Linux LVM")

specifically, i have two old IDE hard drives that i need to format into the "Linux LVM" (code 8e) file system to add them to my current LVM pool (which now sits at 1 drive, so it's gonna be at 3 once i format these two drives)

does anyone know either:

- what's the CLI-based "gui" i am talking about?
- what's the "mkfs.___' command for formatting to Linux LVM (instead of just ext2 / ext3)?

---

### Post by taurus on 2008-02-28
```
sudo cfdisk **/dev/sda**
```
Replace /dev/sda with the actual drive that you want to make changes to.

---

### Post by bluepowder7 on 2008-02-28
bingo!  thank you!  that's precisely the one i was trying to find.  i gotta write some of these commands / tools down somewhere, since i sometimes stumble on some really good useful bits.

thanks again! :)

---

