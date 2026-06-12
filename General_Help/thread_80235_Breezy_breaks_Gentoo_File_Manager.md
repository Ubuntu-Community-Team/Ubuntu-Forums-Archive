---
title: "Breezy breaks Gentoo File Manager"
date: 2005-10-21
forum: General Help
---

### Post by marcw on 2005-10-21
My favorite file manager, Gentoo, no longer works when installed in Breezy.  I am unable to delete, move or copy files.  Without those functions, it's worthless.  Here's what I've tested for so far:

1) Upgraded install (from Hoary, where it worked fine)
2) Fresh install with LVM
3) Fresh install w/o LVM
4) Standard Ubuntu package with all of the above
5) Compiled from latest source with 2 & 3 above.

The results are all the same.  Gentoo sees the files fine.  It just complains when I try to move (or delete or copy) a file that the file doesn't exist.  I loaded a couple other FMs that don't seem to have this problem.  Neither does Nautilus.  But I don't want to use any other FM besides Gentoo if I have a choice.

This sounds like a Gentoo problem, you might be saying.  It might be.  But it sure works fine on Hoary and FC4.  What on earth could make it behave this way?  I'm stuck...  Thanks for any pointers.

---

### Post by marcw on 2005-10-31
After doing some investigating with the Gentoo author, it seems that Breezy did indeed introduce a compatibility issue with Gentoo.  The Ubuntu package is indeed broken for Breezy.  The easy fix (for now) is to compile manually with the configuration switch "--disable-nls".  (Of course this will render Language Support invalid).  The author has also posted a patch in the Gentoo mailing list.

---

