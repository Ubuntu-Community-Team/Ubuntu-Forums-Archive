---
title: "Openoffice.org toolbar display problems"
date: 2007-04-09
forum: General Help
---

### Post by rayamberg on 2007-04-09
Hello,
I am currently having a display problem that occurs in my Openoffice.org v2.02 (the package is openoffice.org 2.0.2-2ubuntu12.3).  I am running Ubuntu Dapper Drake and I have an Nvidia Geforce FX 5200 running on the 'nv' driver for Ubuntu.  I don't seem to have this problem in any other program.

The basic problem is that buttons and menus on the toolbar appear and disappear.  The volatility is especially strong when the mouse cursor highlights a particular button.

I have two snapshots of the problem here:
[Snapshot 1]("http://www.cs.ucr.edu/~ramberg/snapshot1.png")
[Snapshot 2]("http://www.cs.ucr.edu/~ramberg/snapshot2.png")

Notice that some buttons appear in snapshot1, and others in snapshot2, while some disappear.  Notice that many buttons are gone in snapshot1, when I clicked a menu.

This problem makes navigating through Openoffice a bit difficult.

Any ideas?  Thanks in advance for the help.

Sincerely, Ray Amberg

---

### Post by WiseElben on 2007-04-10
Did this just started happening? I don't really know how this could happen, but you say that the icons reappear, so it leads me to believe that means you didn't delete some files, which is a good thing. I, however, would also try a remove and reinstall. Also try deleting your .openoffice.org2 folder in your home folder. One more thing: It might be a screwed up GTK theme, so try changing to a different one.

Other than that, I have no idea.

---

### Post by Hallvor on 2007-04-10
Maybe this thread will help:

[http://ubuntuforums.org/showthread.php?p=2407507](http://ubuntuforums.org/showthread.php?p=2407507)

---

### Post by rayamberg on 2007-04-12
I'll try the suggestions out and will report the results back here.  Thanks.

---

### Post by rayamberg on 2007-04-17
I removed the openoffice.org-common files (which also removed the core packages and other programs), and reinstalled.  It is working correctly now.  Thanks for the help.

---

### Post by alpavi on 2008-03-16
> **rayamberg said:**
> I removed the openoffice.org-common files (which also removed the core packages and other programs), and reinstalled.  It is working correctly now.  Thanks for the help.

uninstall/reinstall worked beautifully.  good call.

---

