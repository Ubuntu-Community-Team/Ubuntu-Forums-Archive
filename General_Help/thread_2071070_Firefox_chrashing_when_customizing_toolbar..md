---
title: "Firefox chrashing when customizing toolbar."
date: 2012-10-14
forum: General Help
---

### Post by Ravi5kumar on 2012-10-14
I recently updated to Firefox 16 and facing the problem. Whenever I open customize toolbar window and drag a tool to the toolbar the whole Firefox hangs! Anyone experiencing this problem? Any fix for that?

---

### Post by dniMretsaM on 2012-10-14
Open FF in safemode (run the command [FONT=Courier New]firefox --safemode[/FONT]) and try customizing the toolbar. If it doesn't crash, then the problem is one of your addons. Disable them all and re-enable them one by one until it starts crashing again, and you have your culprit.

---

### Post by Ravi5kumar on 2012-10-14
Thanks [dniMretsaM]("http://ubuntuforums.org/member.php?u=1268161")! The real problem was one of the addon that causing the crashing! The culprit was the addon named 'Smartest Bookmarks Bar 1.1'. I disabled it and now Firefox no more hangs when I customize toolbar...

---

