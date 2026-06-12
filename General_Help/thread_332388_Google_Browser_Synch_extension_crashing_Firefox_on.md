---
title: "Google Browser Synch extension crashing Firefox on startup"
date: 2007-01-06
forum: General Help
---

### Post by Levander on 2007-01-06
Is the Google Browser Synch working for anyone?  It's crashing Firefox about half the time on startup for me.

I've removed the extension using Firefox's Add-Ons dialog, as well as manually removing it from the firefox extensions directory in my home folder.  Every time I reinstall it, it starts crashing again.

And, even when Firefox doesn't crash, the extension doesn't work.  When I click on the icon for the extension on the right hand side of the Firefox toolbar, the menu that is supposed to pop up doesn't.  And, nothing works on the extension's Preferences dialog that you get to via Firefox's Add-Ons dialog.

This brief bug report is the only thing I've found about it on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/75859](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/75859)

---

### Post by Levander on 2007-01-07
It was something in the user profile.  I know I had tried this before, but just getting rid of the .mozilla directory and reinstalling the extension worked fine, the 2nd time I tried it.

Luckily that extension backs up all my cookies and bookmarks, so there's very little work getting everything back the way it was.

---

