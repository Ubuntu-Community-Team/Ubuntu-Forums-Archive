---
title: "kdeinit is filling my hard drive"
date: 2007-05-02
forum: General Help
---

### Post by VernerVonTux on 2007-05-02
where do kde / kdeinit log files go, because I believe kdeinit or something to do with kde is causing my hd to fill with log files because the filling of my hard drive stops when I kill an "uniteruptable" kdeinit process and any other sleeping or otherwise kdeinit processes(except this time as my hd is filling right now even after killing the kdeinit processes);however, I just can't seem to find the culprit files that are being written so that I can delete them, does anyone have any suggestions, also, what is the correct way to check the integrity of the hd using fsck? I am running ubuntu 6.10 with gnome as my default session and I often run kde programs from gnome, especially yakuake. I didn't have any real problems with kdeinit until I had installed "brutalchess" and "Balazar", is there any possible connection?

---

### Post by VernerVonTux on 2007-05-05
OK, perhaps adding more information on my problem will help:

I ran an fsck via live-cd, and my hard drive has 1.5% non-contiguous blocks. What makes this odd is the fact that after deleting some video files I finally did manage to log into Ubuntu for a while, but had to give up using kde software because whenever I do, the kdeinit process somehow fills my hard drive with unlocatable files ;however, just yesterday when I tried to log in, gdm kicked out an error letting me know that it could not write a file (forget the name) required to log in. This is the same error that I would get when my harddrive would fill when I ran kde applications ;however, the last time I shut down, my hard drive had 2.9 gigs free. What is going on? The integrity of my Windows partition (ntfs) seems undamaged and frankly 1.5% non-contiguous files really doesn't seem like enough of an integrity problem for this total crash of my linux partition. With this added information does anyone have any idea what is going on? Any help would be greatly appreciated as soon as possible :)

---

### Post by nikhilk on 2007-05-05
> **VernerVonTux said:**
> however, just yesterday when I tried to log in, gdm kicked out an error letting me know that it could not write a file (forget the name) required to log in.
This could mean that your /home partition is getting full. Did the 2.9 gigs of free space you mentioned were on your /home partition? Try the command
```
du -sh /home/*
```
to see where most of the disk space is being used up.
kdeinit is an essential KDE process that is required to launch any application under KDE. I do not know exactly how it works in GNOME session though.

---

