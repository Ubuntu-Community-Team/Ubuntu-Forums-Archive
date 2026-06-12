---
title: "How do I downgrade a buggy package?"
date: 2007-10-31
forum: General Help
---

### Post by mamadu bwana on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/158270](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/158270) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi

After upgrading to Gutsy Gibbon GIMP was screwed up ([details in my initial post]("http://ubuntuforums.org/showthread.php?t=587556")). Turns out, its a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/158270") which has yet to be fixed.


 After looking up the how to "downgrade" a package I found that the first step is to uninstall the offending package using Synaptic.  However, Synaptic indicates to me that if I remove Gimp it will also remove 'ubuntu-desktop'.  Does it mean the entire Ubuntu Desktop?!?!

Needless to say I do not want to remove my entire desktop, nor do I want to compromise my system or any future installation of an upgraded and (hopefully) debuged version of Gimp.

But in the meantime, I really need Gimp.  What should I do? Can I _safely_ downgrade only the Gimp package and, if yes, how?

Thanks!

---

### Post by dpar on 2007-10-31
I believe that the ubuntu-desktop that it wants to remove is really only a metapackage, which really doesn't hold any files.

Read this link......[http://ubuntuforums.org/showthread.php?t=104735&highlight=remove+ubuntu+desktop](http://ubuntuforums.org/showthread.php?t=104735&highlight=remove+ubuntu+desktop)

---

### Post by MrFSL on 2007-10-31
If you have a deb package which is an older version and you are wish to downgrade the deb package management can handle it without uninstalling the newer version.

---

