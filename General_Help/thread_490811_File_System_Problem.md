---
title: "File System Problem"
date: 2007-07-02
forum: General Help
---

### Post by RelativelyQuantum on 2007-07-02
Hi all. 

I'm having a little trouble with the file systems on my Sony Vaio. When I try to boot into my Ubuntu partition, and my computer does the standard file system check, it discovers corrupted systems and does not allow my to access my desktop. The only way I can interact with my computer afterward is through a command prompt. Is there any way to repair the systems through the command prompt, or otherwise deactivate the check, as the corrupted systems hadn't visibly effected the computer's performance while they were there.

Cheers!

-Quantum

---

### Post by rillip on 2007-07-03
At the command prompt, have you tired typing

```
sudo startx
```

This should launch the DE you are using.

As for actually repairing the system, if you're getting an error like this, it should be running fsck.  If you needed to you could run it manually but it should be doing this on it's own.  Some more information about the error might be useful.

---

### Post by RelativelyQuantum on 2007-07-10
Thanks for the info. In the end I discovered that a part of my hard drive is actually damaged, and surmounted the problem by reinstalling edgy into a partition toward the edge of the disk (away from the damaged part). It seems to be working perfectly now, and I have run fshk to make sure of this.

As always, thanks for  the help!

---

