---
title: "Folder that is mounted goes away? strange screenshot"
date: 2007-04-09
forum: General Help
---

### Post by Underpants on 2007-04-09
I have a folder called "bluebox-data" that is in my home folder. 

Recently, the folder has been "locking up" or "disappearing" I mean, something is there, but it takes forever to get a directory listing either from the terminal or a GUI. I mount my servers data share into this folder. If I restart, the folder is fine and the data is mounted. But it will shortly go away..

I'm not sure what's causing it...

I mount the folder using fstab:
```
# Mount bluebox-data to
//192.168.1.10/bluebox-data /home/aaron/bluebox-data smbfs credentials=/home/aaron/.smbpasswd,uid=aaron 0 0

```

Here's what it looks like:
[IMG]http://waxgroove.com/folder_problem.png[/IMG]

---

### Post by yabbadabbadont on 2007-04-09
If you have previews (thumbnails, item counts, ...) turned on, make sure that they are enabled for local files and directories only.  I'm guessing that the problem is because it is a network mount.

Edit: never mind, I just saw that you said that it happens in the terminal too.  :?

---

### Post by Underpants on 2007-04-09
This is a recent happening. It's been fine for months.... I don't recall changing that setting. I should note that the previews are on, and I like having them on very much. They've always been this way. Whenever the folder is in this state I cannot open it or use it.

---

