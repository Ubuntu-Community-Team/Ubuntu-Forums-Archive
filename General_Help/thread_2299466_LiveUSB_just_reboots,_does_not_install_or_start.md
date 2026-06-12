---
title: "LiveUSB just reboots, does not install or start"
date: 2015-10-18
forum: General Help
---

### Post by nfmcclure on 2015-10-18
See this thread about how I can't get my drivers to work on my graphics card and am now stuck in a login loop:
[http://ubuntuforums.org/showthread.php?t=2297690](http://ubuntuforums.org/showthread.php?t=2297690)

I would like to start over with a fresh install, so I made a liveUSB disk via:
[http://unetbootin.github.io/](http://unetbootin.github.io/).  I used the Ubuntu 14.04.3 desktop 64bit ISO.

I checked for errors, but none were found, and I've even downloaded and reinstalled a few times to be sure.

When I choose the USB from the BIOS, it gives me a few options.

1)  When I select Install Ubuntu, it starts to load up and then, without an error or message, just reboots the whole machine.
2)  When I select try Ubuntu without installing, the exact same thing happens (no error message).  Just a reboot.

How can I reinstall Ubuntu from scratch?  When I get to my regular login screen, it gets stuck in a login loop.   I've tried many many many possible solutions to log in, and none work.  I can hit CTRL+ALT+F1 and log into a terminal screen that way.  Is there a command line way to get to install ubuntu from scratch?

Thanks.

PS- I'm dual booting Ubuntu14.04 and Windows 10.  The windows 10 partition works wonderfully and I've tried to wipe the linux partition via windows, but it doesn't work either.

---

### Post by sudodus on 2015-10-19
Have you tried with the boot option nomodeset?

---

