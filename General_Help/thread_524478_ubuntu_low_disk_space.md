---
title: "ubuntu low disk space"
date: 2007-08-13
forum: General Help
---

### Post by newbie2expert on 2007-08-13
how do you know where your space has been allocated? 

I installed ubuntu with about 4GB of space and everything was ok till i ran out of about 2GB or so. 

I searched the file system to remove any big files but all the big files i deleted didnt make the slightest difference to the disk space. I tried uninstalling programs which didnt help either. 

I am going to reinstall ubuntu because i prefer it to windows but i need to know what how much disk space i shud allocate to the partition and how I can tackle freeing up disk space if i run into the same problems again. Also are there any softwares that can assist in viewing where most of my space is allocatd?

---

### Post by heimo on 2007-08-13
I think there's Disk Space Analyzer or something like that installed by default in Feisty Fawn (7.04). Remember to empty your Trash after deleting files, or they'll still take space. You could also empty package cache by running:
```
sudo apt-get clean
```

I think around 8-10GB for Ubuntu is good, especially if you have separate /home partition (which is recommend).

---

### Post by 1/0 on 2007-08-13
I don't like installing software for stuff that's already there, so if you don't want those sytem requiring GUIs, just open a shell and check with:

```
sudo du -s /*
```
and
```
df -h
```

Clean up stuff in /tmp. Ubuntu is not a good distro for small space. You could [clean up installed files]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html").

You got [some better ones at that.]("http://bengross.com/smallunix.html") 

For Xubuntu I would use a root partition of at least 4 Gb plus swap and /home.

---

### Post by heimo on 2007-08-13
Applications->Accessories->Disk Usage Analyzer

---

