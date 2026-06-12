---
title: "Strange mounting problem"
date: 2006-07-18
forum: General Help
---

### Post by bogoliubov on 2006-07-18
Hello. A couple of days ago I bought a cheap no-name mp3 player. I took it home and plugged it into my computer; the thing was mounted and everything work ok. Unfortunately the mp3 player wasn't working correctly so I had i replaced for a new (identical) one today. 

Now when I plug it in it will only be in read-only mode; which is kinda useless. What's happening and how can I change this?

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **bogoliubov said:**
> Hello. A couple of days ago I bought a cheap no-name mp3 player. I took it home and plugged it into my computer; the thing was mounted and everything work ok. Unfortunately the mp3 player wasn't working correctly so I had i replaced for a new (identical) one today. 

Now when I plug it in it will only be in read-only mode; which is kinda useless. What's happening and how can I change this?
What is the filesystem type of the mp3 player ? NTFS ? It should be specified in the manual.

---

### Post by bogoliubov on 2006-07-18
> **xXx 0wn3d xXx said:**
> What is the filesystem type of the mp3 player ? NTFS ? It should be specified in the manual.

I think it's FAT; when I plug it in and check System->Admin-Discs it says
Windows virtual fat (vfat)...

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **bogoliubov said:**
> I think it's FAT; when I plug it in and check System->Admin-Discs it says
Windows virtual fat (vfat)...
Are you using a custom kernel ? Like one you compilied ?

---

### Post by bogoliubov on 2006-07-18
> **xXx 0wn3d xXx said:**
> Are you using a custom kernel ? Like one you compilied ?

Not one I've compiled no, but it's optimized for Athlon:
$ uname -a
Linux ubuntu 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux



But it worked with the old mp3 player!

---

### Post by bogoliubov on 2006-07-18
Hmm, now it worked! I didn't do anything differently; just plugged it in as usual...

Good, but strange...

---

### Post by Skia_42 on 2006-07-18
I have had that happen with my old Rio. Restarts solve more problems then you think...

---

### Post by bogoliubov on 2006-07-19
> **Skia_42 said:**
> I have had that happen with my old Rio. Restarts solve more problems then you think...

Yeah, but I thought that that mainly applied to windos stuff :)

---

### Post by bogoliubov on 2006-07-19
> **Skia_42 said:**
> I have had that happen with my old Rio. Restarts solve more problems then you think...

Hey, I think I figured it out. If I use "HOLD" on the mp3 player the filesystems is read-only! I'm probably stupid but I'd never thought the HOLD button had anything to with this... :)

---

