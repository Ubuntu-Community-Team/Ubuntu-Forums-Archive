---
title: "Where is App Info Saved?"
date: 2007-03-08
forum: General Help
---

### Post by 64mgb on 2007-03-08
Where does Ubuntu save information about applications?  Is there a repository similar to the Windows registry?  Or does each app keep track of it's own information?  I'm trying to completely uninstall Lazarus and start over, but every time I reload it and then restart it, it still remembers the packages that were loaded before.

Thanks,
Rich

---

### Post by DagMan on 2007-03-08
If you mean you remove it then reinstall it, then maybe try "comletely remove" in synaptic as this will remove configuration files for it as well while just removing doesn't.  At the command line this is sudo apt-get remove --purge
I don't know if this is what you were looking for though, I don't even have that package in my package manager.

---

### Post by 64mgb on 2007-03-08
Thanks for the input DagMan...I think I just figured this out.  I've been using Linux for about 9 or 10 months now, but I'm still learning.  It just dawned on me that most apps tend to save a hidden config file in your home folder, so I looked there, and sure enough there is .lazarus folder in my home folder.  I'm pretty sure that if I remove that before I reinstall it will be a completely new install.

Rich

---

### Post by scxtt on 2007-03-08
any file in ~/.lazarus is specific to your user - so it won't have much bearing on the program as a whole ... that would be /usr & /usr/lib (for the most part) ... adding a "--purge" flag should take care of that ...

"Purge <package>: remove it and all its associated configuration and data files."

---

### Post by 64mgb on 2007-03-08
> **64mgb said:**
> Thanks for the input DagMan...I think I just figured this out.  I've been using Linux for about 9 or 10 months now, but I'm still learning.  It just dawned on me that most apps tend to save a hidden config file in your home folder, so I looked there, and sure enough there is .lazarus folder in my home folder.  I'm pretty sure that if I remove that before I reinstall it will be a completely new install.

Rich
This did it...first I did "Mark for complete removal" in Synaptic, then I deleted the .lazarus folder in my home folder, then reloaded Lazarus.  It resulted in a fresh install.

Rich

---

