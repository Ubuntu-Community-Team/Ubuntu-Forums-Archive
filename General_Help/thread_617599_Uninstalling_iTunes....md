---
title: "Uninstalling iTunes..."
date: 2007-11-19
forum: General Help
---

### Post by kguthrie on 2007-11-19
I was trying to get iTunes to run on Wine earlier today, but I kept having an issue with the screen being painted black, and so I have opted to just uninstall it and find something else that fits my needs, but now I can't uninstall it.  I run the uninstaller in Wine, and when I click remove, it starts reinstalling itunes?  At the end, it tells me the installation has finished, but that isn't what I want at all!  It seems I can't get rid of it apart from just deleting the directory in Program Files, but that still leaves a bunch of broken shortcuts in the Wine menu...anyone have any idea of what I can do or what I am doing wrong?  Thanks!

---

### Post by =velkyn= on 2007-11-27
I have exactly the same problem.

I opted to delete manually Apple Update, Quicktime and iTunes from  .local/share/applications/wine/
and delete all the related folders in the virtual Drive C in .wine/drive_c/Program Files/

not an elegant solution, especially because if I run $uninstaller the entries are still there :(
but at least I save some space on the hard drive.
any further idea?

---

