---
title: "My ext3 hard drive inaccessible, says it's fat32 [Resolved by OP]"
date: 2006-11-21
forum: General Help
---

### Post by Shay Stephens on 2006-11-21
This one has me stumped big time.  I have a data drive that was formatted as ext3 about a month ago.  I dual boot with windows, and was using an ext3 driver to access the drive from windows.  The driver program is called ext2IFS.

All was working fine until tonight when I could no longer access the drive from ubuntu or windows.  I ran some forensics programs in helix boot cd, and it sees the drive as fat32.  Windows sees the drive as unformatted and won't do anything with it.  Ubuntu can't do anything with it either.

I am at a loss as to which direction to go to pull off info from the drive.  I hope it's not dead.  But if anyone has a clue as to what this is or can point to some help, I would be very grateful.

---

### Post by aysiu on 2006-11-21
Maybe you can try [using *dd_rescue*](http://www.tivocommunity.com/tivo-vb/showthread.php?postid=2165825#post2165825)?

---

### Post by Shay Stephens on 2006-11-22
Thank you so much for the link.  I was booting to try it out when the startup routine ran an fsck on the drive.  It mentioned something about a handfull of htree inodes that were bad and cleared them.  When ubuntu booted up, the drive was readable again!

So the problem is fixed, but I never had a chance to try your link.  But I have placed it in my notebook of knowledge :-)

Thanks again!

---

