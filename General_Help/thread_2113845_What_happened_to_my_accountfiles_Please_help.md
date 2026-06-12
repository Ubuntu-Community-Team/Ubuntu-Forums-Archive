---
title: "What happened to my account/files? Please help"
date: 2013-02-08
forum: General Help
---

### Post by Miles78 on 2013-02-08
I accidentally deleted one of my panels. To restore it, I followed some instructions that I found typing the following into the terminal:

gconftool-2--shutdown
rm -rf~ /.gconf/apps/panel
pkillgnome-panel

after typing the second command, my desktop (background) turned black and the items (folder/files) disappeared one by one. After restarting the system all my personal files were gone!! The installed programs seem to run fine but all 'recent file' entries in their menus are empty. What happened? How can I restore my previous settings? How do I get my files back?
I am using ubuntu 11.04
Thanks a lot!

---

### Post by landersohn on 2013-02-08
are your files gone or just the entries in "Recent Files" ?

---

### Post by Miles78 on 2013-02-08
No, I can't find any of my files or folders. It seems as if I have a fresh account.

---

### Post by Cheesemill on 2013-02-08
If those are the exact commands you typed in then you've deleted all your files because of a typo.

The actual command should have been
```
rm -rf ~/.gconf/apps/panel
```instead of
```
rm -rf ~ /.gconf/apps/panel
```Because you put an extra space after the ~ then instead of deleting the directory ~/.gconf/apps/panel you told rm to delete the directories ~ *and* /.gconf/apps/panel

/.gconf/apps/panel doesn't exist so it wouldn't have been deleted, but ~ is a shortcut for your home directory so you've deleted it completely.

If you need to try and recover anything then stop using the drive straight away, the more you use it the more you will write over your old files.

Searching the forums for testdisk or photorec should find you some threads outlining how to recover your data.

---

### Post by Miles78 on 2013-02-08
Oh no!
I will try if I can do it on my own. I am afraid though I will need someone to guide me somehow through this process. I am too much of a beginner with Ubuntu......

Thank you for explaining!

---

