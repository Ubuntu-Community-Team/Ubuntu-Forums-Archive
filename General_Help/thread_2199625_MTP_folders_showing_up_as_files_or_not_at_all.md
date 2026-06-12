---
title: "MTP folders showing up as files or not at all"
date: 2014-01-14
forum: General Help
---

### Post by BitJunkie on 2014-01-14
I've searched around but can't seem to find a solution to my problem.

I'm running Ubuntu 12.04 and I have installed the backported gvfs from the [FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]langdalepl/gvfs-mtp PPA to allow mtp access. When I plug in my Moto X (running Android 4.4, stock, un-rooted) it is detected and mounts OK. But a few of the folders are listed as regular files both in nautilus and the command line. The permissions [/FONT][FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace](Android permissions, e.g [/FONT]drwxrwx--- root     sdcard_r          2014-01-14 18:28[FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]) [/FONT][FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace]on the folders[/FONT][FONT=Ubuntu Mono, Ubuntu Beta Mono A, Consolas, Bitstream Vera Sans Mono, Courier New, Courier, monospace] in question are the same as other folders that show up fine. 

The problem seems to be with folders that have a recent date, like after Dec 1, 2013. From an Android shell, I used the "touch" command to change the date on one of the folders (to the current date and time) and it disappeared altogether in nautilus. It doesn't even show up as a regular file anymore. Unfortunately, when I try to use "touch" to set the date prior to Dec 1, I get "operation not permitted" so I can't say for sure if the date is even related or not. 

Any ideas? Does gvfs have a cache somewhere I can clean?[/FONT]

---

