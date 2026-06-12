---
title: "Install popcorn-time.se v3.2 issues"
date: 2015-10-30
forum: General Help
---

### Post by heepie202 on 2015-10-30
(similar thread --> [http://ubuntuforums.org/showthread.php?t=2268409](http://ubuntuforums.org/showthread.php?t=2268409))

After the recently defunct of [popcorntime.io]("https://popcorntime.io/"). I've looking for alternative. The best solution at the moment seems to be [popcorn-time.se]("https://popcorn-time.se/"), but I've been having issues with installation. After downloading the zip file for Linux from their website and running it; the splash screen starts but after that I just get a black screen with nothing else to go on with. Initially I got this error "**Error missing libudev.so.0"**, which got solved with this solution:

For 32bit
# sudo ln -sf /lib/i386-linux-gnu/libudev.so.1 /lib/i386-linux-gnu/libudev.so.0 For 64bit

 # sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0 The output from the CLI is this:

 $ ./Popcorn-Time 
Gtk-Message: Failed to load module "overlay-scrollbar"
[30379:1030/143751:INFO:gpu_info_collector_x11.cc(80)] NVCtrl extension does not exist.
[30379:1030/143752:INFO:simple_index_file.cc(437)] Simple Cache Index is being restored from disk.



I also notice they had new releases for the Mac and Windows but not new releases for Linux. Mac and Windows are at 5.4 while Linux still stuck at 3.2. Have they deprecated the Linux version?
I thought on downloading the source code and compile it myself but their building instructions are only available for Mac or Windows. Another reason to think Linux version has been deprecated.

Does anybody has a solution for this, may be even another alternative? I know about [ButterProject]("http://butterproject.org/"), but this still under development.

---

### Post by a-lendrum on 2015-11-19
I've had the same issue. Temporary solution has been to boot to windows when I want to watch a movie...less than ideal.

---

### Post by Bucky Ball on 2015-11-20
After staff discussion

*Thread closed.*

The forums do not give support for applications which infringe copyright or ToS. Popcorntime, in many cases, infringes copyright. 

If you wish to discuss this further please post in the Resolution Centre. Thanks.

---

