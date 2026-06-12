---
title: "[SOLVED] Synaptic Package Manager and new versions"
date: 2008-06-01
forum: General Help
---

### Post by brett123 on 2008-06-01
Sorry, I've posted something similar before, but it never led to any result.

I am very new to Linux (which is probably all of the problem I know) and am very frustrated by one aspect I cannot get a simple answer to: what do I do when Synaptic Package Manager doesn't have the most recent version of something?

Specifically, at the moment I cannot install:
- Sunbird 0.8 (can download it, extract, but then have no idea what to do)
- gcaltool 5.23.1 (ditto above, extracted but then what???)

There are bugs in the existing versions of these two applications that I just cannot live with. But I don't have the knowledge of how to just update them? Surely it can't be that difficult if I can find the correct version and download it!?!???! Can it???  :|

---

### Post by ad_267 on 2008-06-01
This is a useful read: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

If you can you want to download a .deb file which is a debian package and then you can uninstall using synaptic and the old version is updated.

How you install depends on what's in the archive. If it's source code then you need to compile it. There should be an INSTALL file or similar in the archive that tells you how to install.

---

### Post by brett123 on 2008-06-01
Many thanks. That reply in itself helps alot.

Next question: So, only .deb packages can be (easily) dealt with in my case? And if I can't find .deb that means I should stay away from it until such time as I learn to compile stuff (months away)?  Is that the crux of the matter here?

---

### Post by ad_267 on 2008-06-01
Yes .deb files are the easiest to deal with but installing something like sunbird shouldn't be too hard. It's a lot easier if you have a little bit of an idea about how Ubuntu works. If you do compile from source code you can use checkinstall so that you can remove or update a package with the package manager.

If the file you download is a precompiled binary (like sunbird) then you can extract it to somewhere like /usr/local which is the place where you usually install software that isn't from the repositories. You will want to uninstall any previous version using with the package manager and create a link to the executable file in /usr/local/bin. This means that if you type in "sunbird" in a terminal or create a launcher in a menu for the command "sunbird" then Ubuntu will be able to find the executable.

In order to extract files into /usr/local you will need root privileges. Hit Alt-F2 and run "gksudo nautilus" gksudo runs a graphical application as root and nautilus is the file manager. Make sure you're careful as you can do anything as root and completely mess up your system if you do something silly.

If you want to create a launcher in the menu for all users you can create a sunbird.desktop file in /usr/local/share/applications

If this program is just for you then you can also just extract it to somewhere in your home directory and create a link to the executable file in ~/bin

---

### Post by brett123 on 2008-06-01
Thanks again. I've tried what you suggested and still can't get Sunbird working. HOWEVER I have concluded my issue may be Sunbird related, and not the process I am following (your steps above). Hence I'm resolving this thread, as I do now (at least) understand where Package Manager fits in.

Small steps, I haven't even decided to keep Ubuntu/Linux yet, and already I'm trying to tweak things. :D

---

