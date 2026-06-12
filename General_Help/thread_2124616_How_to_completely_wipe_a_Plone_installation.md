---
title: "How to completely wipe a Plone installation"
date: 2013-03-11
forum: General Help
---

### Post by psyllex on 2013-03-11
Hi...I installed Plone awhile ago using their unified installer.  Then we wiped it by deleting the Plone folder in /usr/local.  Later we decided to re-install it fresh and use it but it's pulling in data from the last installation.  I can't do something like auto-remove, --purge remove, etc because it used it's own installer.  I've used 'locate' and 'find' to try and find every instance of 'Plone' and delete it from the server.  But after 3 tries, I can't get it to wipe completely.  

Does anyone have any suggestions?

---

### Post by Dreamer Fithp Apprentice on 2013-03-12
Minor nomenclatural point: What you want to do isn't "wiping" at all. You might get more to the point answers with a different title. 

I don't know anything about Plone, even what it does, but most software that is installed with a deb or script or some other kind of installation program comes with an uninstaller also. Try installing it again if you have already removed part of it again and look for an uninstall script or maybe a text file with uninstallation instructions. Failing that, couldn't you just change whatever data from the previous installation that you don't like? If neither of those is possible for some reason you might search for the files by searching for text you have reason to suspect is in them. Search for that text IN the files, not just in the NAME of the file. Or you could look at all files modified in a time frame in which you did the original installation. Or you could just look in likely places like in ~/.config/plone maybe. In the worst case, it doesn't really take all that long to reinstall everything from scratch. If you are lucky enough or foresighted enough to have backed up your system with something like remastersys or fsarchiver before you installed plone you can probably do it in less than 10 minutes and in the worst case shouldn't take you more than an hour.

---

### Post by Impavidus on 2013-03-12
Most likely there are some files in ~/.config/plone or ~/.plone. Also check /usr/local/{bin,share,etc}/plone. I don't expect files anywhere else, as this was a manual installation in /usr/local/.

---

