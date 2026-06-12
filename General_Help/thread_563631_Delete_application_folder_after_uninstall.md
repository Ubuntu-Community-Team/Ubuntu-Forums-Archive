---
title: "Delete application folder after uninstall"
date: 2007-09-30
forum: General Help
---

### Post by lightstream on 2007-09-30
After uninstalling an application (using Synaptic via Add/Remove..), is it ok to delete the application's hidden folder in my home directory?

(Basically, I managed to break eclipse by deleting the 'workspace' folder in my home directory because I store my files elsewhere. All that happened was that Eclipse complained about not being able to save the workspace, so I restored the folder from Deleted Items. Since then Eclipse has failed to start complaining that it cannot find certain packages. apt-get --reinstall didn't help, so I'm going to uninstall and reinstall. I want to delete as much as possible of the old install first.)

So is there likely to be any problem with just deleting a folder like this?

Thanks for any help

---

### Post by Anzan on 2007-09-30
If you just use 

apt-get --purge remove softwarename

it should clear out everything.

---

### Post by lightstream on 2007-09-30
excellent mate, thanks !

---

### Post by kerry_s on 2007-09-30
> **Anzan said:**
> If you just use 

apt-get --purge remove softwarename

it should clear out everything.

that won't remove the hidden settings file.

yes, you can delete it.

---

### Post by lightstream on 2007-10-01
> **kerry_s said:**
> that won't remove the hidden settings file.

yes, you can delete it.

Thanks! You're right the purge did not remove the hidden settings file in my home directory, and eclipse would still not start after I did that.

I've now gone ahead and deleted the hidden file manually - hopefully eclipse will be able to start ok next time.

---

