---
title: "Ubuntu opens disks and directories in the browser instead of in Nautilus"
date: 2013-05-30
forum: General Help
---

### Post by atjone on 2013-05-30
for example, when I plug in my external hard drive, google-chrome opens `file:///media/atj/HDD`
When in sublime text and I click `Open Containing Folder` it opens the folder in the browser too.
Any clue to how I could get to the bottom of this ?
I have tried looking into `/usr/share/applications/defaults.list` but `inode/directory` is assigned tonautilus-file-handler.desktop like it should be. So I am really clueless

---

### Post by atjone on 2013-05-30
Up ?

---

### Post by Frogs Hair on 2013-05-30
The default application for opening items can be changed by right click > open with . Applications can also be removed from the list with forget association. I set a wallpaper with Firefox once and all my pictures were opening in FF until the default application was reset .

---

### Post by atjone on 2013-05-31
Yeah, for files with extensions you can do that obviously, but what about a Hard Drive that opens itself in the browser, how do I manage to set a default app for that ?

---

### Post by atjone on 2013-06-03
Up ?

---

### Post by atjone on 2013-06-04
Last Up, I guess :/

---

### Post by howefield on 2013-06-04
Have you tried  System Settings > Details > Removable Media.

---

### Post by atjone on 2013-06-04
I changed all to 'Files' to no avail :/

I just noticed that when I am as root, this problem do not occure. If I want to open a directory from with in an application that is being ran by root, it show it in nautilus as wanted.
I tried formatting and re-installing Ubuntu, with / on a partition and /home on an other, but the problem persisted. And since I only formated / and kept my data in /home, I guess that the files that I would need to edit must be in my home folder.

---

