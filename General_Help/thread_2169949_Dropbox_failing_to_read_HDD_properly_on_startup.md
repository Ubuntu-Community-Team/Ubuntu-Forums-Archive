---
title: "Dropbox failing to read HDD properly on startup"
date: 2013-08-24
forum: General Help
---

### Post by leopheard on 2013-08-24
Hi all,


I'm using Dropbox 2.2.13 on Linux Lubuntu 13.04.


I have the Dropbox folder stored in the root of a separate IDE HDD inside the machine. I have found that Dropbox comes up with a message that the folder is not available on every reboot, until I open file manager and simply look at the drive the folder is stored on.


If I restart DB, it can then view the folder and syncs fine.


Has anyone else had this problem? Is there a workaround? How can I force Linux to at least look at that drive upon startup?

Many thanks

---

### Post by vasa1 on 2013-08-24
I think your issue isn't with Dropbox, *per se*, but with the fact that you've chosen to have it on a drive that isn't "visible" until you look at it via the file manager. I have a similar issue on Lubuntu 13.04 with bookmarks to folders in my external USB drive. Once I click on the drive, the bookmarks are visible till the end of the session. On reboot, it's the same story again.

---

### Post by leopheard on 2013-08-25
[SOLVED]

Think I've got it - simple auto-mount program which does exactly that on startup, I've posted a reply on the Dropbox forum here:[URL="https://forums.dropbox.com/topic.php?id=104643&replies=3#post-563549"]

https://forums.dropbox.com/topic.php?id=104643&replies=3#post-563549[/URL]

---

