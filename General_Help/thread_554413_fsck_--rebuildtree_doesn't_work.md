---
title: "fsck --rebuildtree doesn't work"
date: 2007-09-18
forum: General Help
---

### Post by BLTicklemonster on 2007-09-18
I have a borked file system on a drive here, and I want to see if fscking it up will fix it, but I can't get it to do the above mentioned function.

I try

sudo su

then fsck.reiserfs --rebuildtree /path/todrive

and I get instructions on how to use fsck (the instructions in all instances such as this are wretched, by the way. Don't know if any of you non techies ever noticed it, but they aren't of any use to me)

I'm running gutsy if that helps.

Oh, and if I try -y, I am told the drive is mounted with write permissions. And I can't unmount the drive, because I don't have permission.

Should I just format it and get on with my life?

---

