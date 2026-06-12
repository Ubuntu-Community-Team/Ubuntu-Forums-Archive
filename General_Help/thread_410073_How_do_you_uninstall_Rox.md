---
title: "How do you uninstall Rox?"
date: 2007-04-15
forum: General Help
---

### Post by xinix on 2007-04-15
How do you uninstall Rox?  I followed the instructions on the site to install Rox.  I followed the instructions to set it up as a session for all users.  That went well but I didn't really like it. So, I'd like to remove Rox from my system.  Problem is that I cannot find any documentation for uninstalling Rox from my system.  I get the impression that I'm going to have to manually remove files.  Where can I find these, or is there a better, proper, wayt to uninstall Rox?
Thanks

---

### Post by M$LOL on 2007-04-15
Can you point me to the guide you installed it from?

---

### Post by xinix on 2007-04-15
[http://rox.sourceforge.net/desktop/ROX-All]("http://rox.sourceforge.net/desktop/ROX-All")

---

### Post by M$LOL on 2007-04-15
Correct me if I'm wrong, but the only thing the installation guide does is download ROX-Filer to ~/ROX-All 1.1, so if you delete that dir and everything you extracted from the tar archive it should be removed. To remove the 0launch thing, type [COLOR="Red"]sudo dpkg -r 0launch [/COLOR].

---

### Post by xinix on 2007-04-15
Sort of, once you extract the Rox archive and run 0launch, in  this case in the rox-sessions folder, zeroinstall-injector downloads other files and installs them to your system.  Some of them go into ~./cache, another goes into /usr/local/sbin, it also adds a session to your xsessions so that you can log into a rox desktop.  I'm trying to figure out where if any other files were installed.

The folder that you get from extracting the rox-all file can be deleted and you still have rox installed on your system.  For a project as old as this one I and amazed that there isn't any info for uninstalling in the faq.

---

