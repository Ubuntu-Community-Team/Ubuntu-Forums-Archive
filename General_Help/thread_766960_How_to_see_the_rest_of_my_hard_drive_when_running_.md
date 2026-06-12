---
title: "How to see the rest of my hard drive when running 8.04 in Wubi mode"
date: 2008-04-25
forum: General Help
---

### Post by brodymcd on 2008-04-25
To all:

NEWbie here and glad to be on board! I don't even yet know why I love the vibe of Ubuntu, Linux, and open source, but I have been obsessed with exploring it. I downloaded 8.04 and installed in on my XP machine via WUBI. When I boot into Ubuntu, I can see my external HD, but none of the files that are on my C drive... just the root folder, etc. How can I get at the files on the "rest" of my main HD where Unbuntu/Wubi installed?

Thanks!

Brody

---

### Post by knutschr on 2008-04-25
I think this might help:

> How do I access the Windows drives?

The Windows partition where you installed Wubi is available as /host within Ubuntu All the other partitions will be available under /media/

If you are using Wubi-7.04 (7.10 and 8.04 users can skip this), write support for ntfs is disabled by default, to enable it:

   1.

      Make sure you have internet access (see the network icon on the top right)
   2.

      Open the "Applications" menu and select "Add/Remove..."
   3.

      In the listbox on the right select: "Show All Available Applications"
   4.

      Search for "NTFS" and select "NTFS Configuration Tool". Click OK to install it
   5.

      Run the configuration tool under Applications > System Tools > NTFS Configuration Tool
   6.

      Select "Enable write support for internal device". Click OK to set it up.


(Copied from [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide))

---

