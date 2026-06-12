---
title: "Kernel panic with the last five kernel updates"
date: 2015-08-31
forum: General Help
---

### Post by ineuw on 2015-08-31
Installed Xubuntu 14.04 32bit version with EUFI boot on a six month old Acer with 64bit Intel processor laptop. Beyond kernel version 3.13.0.57 every kernel update 58, 59, 60, 61, and 62 fail with a kernel panic. What information could I provide to resolve this issue and where would this info could be found? Since I retained version 3.13.0.57 the laptop functions still but each time Xu is updated, version 3.13.0.62 is reinstalled.

---

### Post by XBNCPRk on 2015-08-31
Give the instructions from [ https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html]("https://help.ubuntu.com/lts/serverguide/kernel-crash-dump.html")  a try, and see if you can pull any of the logs associated with your errors.

A piece of advice - some of the log files you will be going through will be ridiculously long. Taking note of the system time when the crash occurs will make it far easier to find the lines youre looking for that refer to the problem.

---

### Post by ineuw on 2015-09-13
It took me a week to get access to the laptop - installed thel crash tracking & generating software as outlined in the ubuntu documentation and added "nomodeset" to the boot parameters which also had the original "acpi quiet splash" specified. At the same time, Xubuntu update added the 13.0.62 kernel and this booted properly a couple of times and then the kernel panic returned . . . and after a few minutes it boots into the advanced repair mode, and the reboots into xubuntu. So I copied out the generated crash report and pasted it on pastebin, without the crash dump.
  
[http://pastebin.com/Nk7dWJa9](http://pastebin.com/Nk7dWJa9) _usr_bin_skype.1000

[http://pastebin.com/jnYFmTd5](http://pastebin.com/jnYFmTd5) _usr_bin_Xorg.0.crash

---

