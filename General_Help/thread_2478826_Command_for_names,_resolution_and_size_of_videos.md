---
title: "Command for names, resolution and size of videos"
date: 2022-09-06
forum: General Help
---

### Post by yayou on 2022-09-06
Hi there,

I'm looking for a command to log in a file the full name, resolution, size (in megabytes or gigabytes) and path of all video files in a tree.

Thanks for reading me.

---

### Post by TheFu on 2022-09-07
I'd write a tiny script.  It would use find and some image-info tool - probably from the imagemagick suite of tools.  Ah ... sorry, I was thinking image files.  For videos, I'd use mediainfo.
If I wanted to get fancy, I might use xargs, but that would depend whether it was 500 files or 5,000,000 files.  xargs has some nice options to specify the number of concurrent processes and how to bunch files into the command.

Because there is a risk this is a homework problem, I'll wait until you post some attempt at the solution.  It is 2 lines with 3 commands.  Learn about 'find'.

[https://askubuntu.com/questions/577421/short-summary-about-video-files-resolution-size-duration-codec](https://askubuntu.com/questions/577421/short-summary-about-video-files-resolution-size-duration-codec) has examples.

---

### Post by yayou on 2022-09-08
Thank you TheFu. In fact I hoped that a good usage of some native commands could do the work but I know now that I must first install mediainfo and probably also FFmpeg. The problem is that I have few remaining space on my Hdd and I must often erase old kernels and run basic clean commands (Autoremove, autoclean, clean).
So before using your recommandations I must first find a solution to my space disk problem.

---

### Post by TheFu on 2022-09-08
> **yayou said:**
> Thank you TheFu. In fact I hoped that a good usage of some native commands could do the work but I know now that I must first install mediainfo and probably also FFmpeg. The problem is that I have few remaining space on my Hdd and I must often erase old kernels and run basic clean commands (Autoremove, autoclean, clean).
So before using your recommandations I must first find a solution to my space disk problem.

If you have 40G, there shouldn't be any issues for the OS, unless /boot/ is on a separate partition which is required when either encryption or LVM are used OR a swapfile is being used.  I'm not a fan of swapfiles.  Much prefer swap partitions, especially in these days that GPT should always be used, so there isn't any real limit on the number of partitions available.

Of course, if there are billions of media files stored in the same partition/file system as the OS, that's just poor planning by the sysadmin. Live and learn.  Always keep media separate from the OS ... and if end users are allowed logins, keep HOME directories on a different file system too.

---

### Post by yayou on 2022-09-08
In fact it's simply because of financial difficulties. I needed at least two Hdd but was obligated to go with only one and it's to tight for all the things I have. I need to see what I can sacrifice to give more space to my Linux partition. I appreciate and I'm totally agree with your advices.

---

