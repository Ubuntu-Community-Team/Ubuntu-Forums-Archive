---
title: "Dual Boot Ubuntu 14 and Windows 7 - Partition Sizes &amp; Format Questions"
date: 2015-09-11
forum: General Help
---

### Post by Andrew_Rivera on 2015-09-11
Hi ):P

I have been an Ubuntu user for a while and I am thinking of installing it on my non-tech savvy friend's computer.

I built his Windows Gaming PC a few years ago. The issue is, since he lacks common sense on the internet, he tends to get himself a lot of viruses/malware/etc. (e.g. Intended to download a video, received an exe file instead, opened it thinking it would be a video :p).

My idea is to have him dual boot Ubuntu 14 for web browsing and email, and Windows for Gaming and music (he is an iPhone user and needs to sync his phone with iTunes).

He only has one HDD and it is 1tb.

I am trying to figure out how to partition it in the most logical way.

He would need a lot of space on Windows due to him having a lot of PC games, but he would also need a lot of space on the Linux side since he tends to download a lot of "videos".

I was considering making the Ubuntu partition (ext4) small, but large enough just for the OS install and to make the Windows NTFS drive large. Maybe everything could just be stored on the NTFS drive since Ubuntu can read/write to NTFS drives with no problem.

I feel that that would be a decent strategy but I am looking to see if anyone has any better ideas. I just feel that I might be missing something and want to be 100% sure of my decision before having my friend work with a new operating system.

Thank you!! :D

---

### Post by yancek on 2015-09-11
15-25GB should be enough for the Ubuntu system provided he doesn't download a lot of software in Ubuntu.  Create a separate partition for his videos or whatever and format it ntfs so that it can be seen and used from windows and Ubuntu.

---

