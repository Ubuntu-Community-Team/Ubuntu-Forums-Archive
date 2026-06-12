---
title: "Mythtv - How do i get multiple storage directories"
date: 2007-06-04
forum: General Help
---

### Post by xmrkite on 2007-06-04
Hello. I have seen that in mythtv 0.21 (the upcoming versions), one of the new features is multiple storage directories. This way, you can have more than one drive for recordings (and not have to use LVM or Raid)

I installed the proper mythtv packages for Ubuntu, but that gives me version 0.20. How do I get the latest release of mythtv. I know 0.21 is not out yet, but I have read that some people are using some sort of svn version, or something like that. How does that work, and is it stable/safe?

Otherwise, are there any ideas on how to use multiple drives without using LVM or raid?

-Thanks

---

### Post by Swab on 2007-06-04
I don't know anything about myth.. but couldn't you just mount the second drive in a directory inside your media directory on the first drive?

---

### Post by xmrkite on 2007-06-04
Unfortunately, mythtv allows for only one directory for all recordings. All recording info (Program name, details, time, etc) is all stored in a mysql database, it's not a matter of just moving files to that sub directory and scanning it like with an mp3 jukebox.

---

