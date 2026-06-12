---
title: "Search for new file in /dev"
date: 2008-03-19
forum: General Help
---

### Post by Gerlads Mod on 2008-03-19
When I plug in my PSP to my computer, it makes 3 files in the /dev dir.
One of them I don't need and the other 2 I only need the file names.

But here's the trick, the 2 important file names are different on others systems.
For instance on my computer the 2 files are sdb and sdb1. But on others systems it could be sdf and sdf1.

So how would searching and obtaining the 2 files names be achieved with a command?

I know dmesg would list it, but I would have to search manually.
I need a way that would just give them to me.

---

### Post by bodhi.zazen on 2008-03-19
What are you wanting to do exactly ?

removable devices are assigned names when you plug them in, and the name of the device (ie /dev/sdxy) may change.

You can set a label on the file system and it will mount by label, or you can mount by uuid

---

### Post by Gerlads Mod on 2008-03-19
I am trying to make a shell script to make a Pandora's battery. (That just downgrades PSP's firmware so you can use the cool stuff)

The guide is here: [http://forums.qj.net/f-psp-pandora-discussion-207/t-guide-creating-a-pandora-on-vista-linux-126194.html#post1856236](http://forums.qj.net/f-psp-pandora-discussion-207/t-guide-creating-a-pandora-on-vista-linux-126194.html#post1856236)

I need the name in the /dev folder for this to work.

---

