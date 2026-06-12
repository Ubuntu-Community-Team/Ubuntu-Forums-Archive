---
title: "[SOLVED] Linux partition full, whats going on?"
date: 2008-06-07
forum: General Help
---

### Post by CanonKen on 2008-06-07
/ taken up 16GB and running out of space- whats going on here, is there anything I can clean up?
I have my home partition seperate so its not my work or documents, I have done "sudo apt-get clean" and that didn't free up much, don't really want to resize the partition unless I have to but thought 17GB would be plenty big enough.
Heres a screenshot of Disk usage analyser

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73283&stc=1&d=1212863267[/IMG]

---

### Post by geirha on 2008-06-07
From that image, it appears that the root user's home-folder has 13GB in it. You might have your home-folders on a seperate /home-partition, but root's homefolder is usually directly on the /-partition. /root would be the obvious place to start cleaning up at least.

See what the following command in a terminal says. It should locate some big files: ```
sudo du -hs /root/*
```

---

### Post by cariboo on 2008-06-07
Check /root you've got 13GB worth of stuff in there. You will have to be root to delete the extra files there. I would suggest installing **nautilus-gksu** before trying anything then navigate to /root, in nautilus right-click on the file you want to delete and select open as administrator then you can do what you need.

You can install nautilus-gksu using synaptic.

Jim

---

### Post by CanonKen on 2008-06-07
> **geirha said:**
> From that image, it appears that the root user's home-folder has 13GB in it. You might have your home-folders on a seperate /home-partition, but root's homefolder is usually directly on the /-partition. /root would be the obvious place to start cleaning up at least.

See what the following command in a terminal says. It should locate some big files: ```
sudo du -hs /root/*
```
It did find some big files - thanks, going to have a clean up now and se how much I can get back

---

