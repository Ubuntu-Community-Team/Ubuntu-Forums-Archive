---
title: "Unusually slow file transfer between drives that are normally fast"
date: 2018-08-09
forum: General Help
---

### Post by UbuntuWho on 2018-08-09
I am trying to transfer thousands of small files in multiple folders from a portable hard drive to the SD card still in my phone, using my Ubuntu computer. Everything was speedy fast (as fast as can be when you're transferring about 20 gigs of small stuff), but with only a few megabytes left, it now has suddenly slowed to a crawl. Transfer speeds were as fast as several megabytes a second; now it's dwindled down to just a few bytes per second! I tried to copy, cut-and-paste, navigate in the folder and batch copy, and I even changed the cables connecting my phone and drive to my computer - no soap. It still is transferring at about a dozen bytes per second. I realize that there are hundreds of folders, each containing more folders and maybe a file or two, and some are just folders containing empty folders. How can I speed up the transfer?

---

### Post by Autodave on 2018-08-09
Are you almost out of space on the SD card?  That can slow it especially if what is on there is heavily fragmented.

---

### Post by UbuntuWho on 2018-08-10
Actually, no. There are several gigs free.

---

### Post by HermanAB on 2018-08-10
There are some horrid performance bugs in the Linux USB stack and the trouble is that you are already running the process, so there is not much that you can do now, that will not interrupt the process, causing everything to start over.

If you need to copy lots of files, then you should use rsync, not cp.

If the copy process is still running, then you can try to ionice it.

However, you said the card is still in your phone, so the trouble can be over there and then there isn't anything you can do now, except wait, or start over.

---

### Post by UbuntuWho on 2018-08-10
> **HermanAB said:**
> If you need to copy lots of files, then you should use rsync, not cp. If the copy process is still running, then you can try to ionice it.
The process has finished, without losing a single file or folder. I can keep this in mind for when I need to do this again. Thanks for the tips.

Since I wasn't actually able to diagnose the problem, this thread is still open for suggestions.

---

