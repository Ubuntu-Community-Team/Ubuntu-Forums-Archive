---
title: "Home Dir"
date: 2007-12-19
forum: General Help
---

### Post by fazavon on 2007-12-19
Ok here is the confusing part

I run df -h and my home dir is 23G with 13G being used and 9.6G free space.

But if I run Disk Analyzer I have only used 1.7G of my 23G of total space.

If I look at Nautilus, the status bar at the bottom, it says I only have 9.6G of free space.

If I select all files and folders (including hidden files and folders) then right click and hit properties it says I only have 1.7G of space being used?

I am at a loss here any help would be great. 

Before you ask, I have a separate Home Dir looks something like this

/ = 65G
/home = 23G
/swap = 4096MB

thanks in advance

//j

---

### Post by bindatype on 2007-12-19
Check the disk usage on home by doing
 
 $ sudo du -kh /home

---

### Post by fazavon on 2007-12-20
This is what is says

1.8G    /home/jbeitler

---

