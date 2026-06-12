---
title: "[SOLVED] Firefox in &amp;quot;Safe Mode&amp;quot;"
date: 2007-08-09
forum: General Help
---

### Post by Zeenomorph on 2007-08-09
I've lost my Firefox menus.  I installed a mini-fox theme, and now I don't have the menu bars to change anything, even the menu to change the theme is gone.  I've uninstalled firefox, and reinstalled it, same problem.  I went to the firefox site and they told me to type 

/path/to/firefox/firefox -safe-mode              in the terminal window.  I did, and it said no file.  I tried typing /home/etc/firefox/firefox safe-mode as well as /etc/firefox/firefox safe-mode but nothing worked.

Can someone give me some advice on how to get Firefox to run in safemode please?

---

### Post by Zeenomorph on 2007-08-09
ummm... hmmm.... this is going to sound funny, but the problem seems to have fixed itself!  I've been messing with this for about an hour, then I typed my question here, and the problem went away!  I guess it's like the fact that your car only runs perfectly when you take it to the mechanic!  Thanx anyway.

---

### Post by aysiu on 2007-08-09
For the future, a simple ```
firefox -safe-mode
``` will do the trick. You don't really need the path.

More details here:
[ HowTo Get Rid of a Corrupt Firefox Profile (and keep the bookmarks)](http://ubuntuforums.org/showthread.php?t=103930)

---

