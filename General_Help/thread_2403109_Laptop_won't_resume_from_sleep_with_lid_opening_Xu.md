---
title: "Laptop won't resume from sleep with lid opening Xubuntu 18.04"
date: 2018-10-07
forum: General Help
---

### Post by Ralph L on 2018-10-07
I just clean installed, on my laptop, xubuntu 18.04 in a new partition leaving my previous partitions containing 16.04 and 14.04.  On Xubuntu 18.04 when I select suspend from the whiskers menu, the computer suspends and resumes fine (when I press the power button to start the resume).  However, if I initiate the suspend by closing the lid, it appears to suspend fine--shuts off fans, blanks screen, and starts the power light blinking orange.  However, when I open the lid, the screen flashes, but then blanks again and just sits there.  If I press Ctrl-Alt-Del and move the cursor, the normal box comes up asking for my password.  When I enter it, the screen blanks and just sits there.  If I do Ctrl-Alt-Del again, the cycle will repeat, but won't resume.  If I use the whiskers menu to suspend, then close the lid, then reopen it, the computer resumes.  It is as if the suspend initiated by closing the lid, does not properly set up for the resume, but a whiskers menu initiated suspend does properly set up for the resume.

This failure started a few months ago, after an update, while I was still running xubuntu 16.04.  Since I still have a working (but not updated xubuntu 14.04), I tried that and "lid closing suspend" and "lid opening resume" worked fine.  So some update in the last few months to 16.04, which was also included in 18.04, is causing the problem.  The computer I am having the problem with is an older computer without uefi: Toshiba Satellite A215-S4697.  I also have a newer Acer Aspire E5-575G-57D4, with uefi, on which lid closing/opening suspend/resume under 18.04 works fine.  So I am guessing the problem has to do with the code changes to support uefi.  Note that I am also having problems with shutdown with the old Toshiba computer and 18.04, that I don't have with the newer Acer.  I posted this problem under a different thread.

Any help is appreciated....

---

### Post by PaulW2U on 2018-10-07
> **Ralph L said:**
> However, when I open the lid, the screen flashes, but then blanks again and just sits there.  If I press Ctrl-Alt-Del and move the cursor, the normal box comes up asking for my password.  When I enter it, the screen blanks and just sits there.  If I do Ctrl-Alt-Del again, the cycle will repeat, but won't resume.  If I use the whiskers menu to suspend, then close the lid, then reopen it, the computer resumes.  It is as if the suspend initiated by closing the lid, does not properly set up for the resume, but a whiskers menu initiated suspend does properly set up for the resume.
Not that this is any help but I've the same problem on a Samsung R620. My Samsung R720 and Toshiba C-50B work as expected. All have Xubuntu 18.04 on them.

I seem to remember the issue was first reported here back in April when 18.04 was released but I've not seen any solution posted. As it's a spare laptop I'm not too worried by the problem. I just suspend using the menus or the power button and have changed the settings so that nothing happens when the laptop lid is closed.

---

### Post by Ralph L on 2018-10-13
I discovered that dropping back to Xubuntu 16.04 with Kernel 4.4.0.97 fixes all the problems.  I believe this was when the solution to the Spectre and Meltdown security holes were fixed and in doing so broke Xubuntu on my Toshiba Satellite A215-S4697. So now I have 4 possible approaches:
1. Find a way to install Kernel 4.4.0.97 into Xubuntu 18.04 or maybe 16.04. Has anybody got any advice if this is possible.  18.04???  16.04????
2.  Find an old version of Xubuntu 16.04.1 that has a kernel version 4.4.0.97 or earlier.  I wrote over my thumbdrive that had Xubuntu 16.04.1 on it.  Anybody know where I can find that. Maybe somebody, that's not as dumb as me, kept a copy and could post it some place, if it is not on the web.
3.  Get the developers to fix the problem in a new version of the kernel. I updated Xubuntu 18.04 with the very latest kernel 4.18.14 and the problem isn't fixed. I have never had luck getting anybody to pay any attention to my bug reports so I don't see much hope there.
4.  Somehow set up grub to automatically boot the os that works.  I can do this manually at boot time by selecting "Advanced options for 16.04...", then scrolling down to the entry "Linux 4.4.0.97".  I don't know how to set up grub so that this is done automatically, and I will never get my wife to accept having to do this each time she boots the computer. Also, with this solution I don't have a backup so I can't reinstall this system if I damage it.  As I said before I overwrote my thumbdrive with Xubuntu 16.04.1 on it.

Any help is appreciated.

---

### Post by Ralph L on 2018-10-21
A little more on solving my problem.  I used Ukuu to install Kernel Version 4.4.0.97 into Xubuntu 18.04.  It is in ppa:teejee2008/ppa.  I installed the ppa using Synaptic.  Once installed it appears in the Xubuntu Main menu>System.  Its pretty obvious how to use it once it is brought up.  There may be a somewhat later version than Kernel Version 4.4.0.97 that will still work with my old Toshiba, but I didn't try to find it.  I may do that at a later date.  So far everything has been working quite well, although this version of the Kernel is quite slow on boot up.

---

### Post by hackerb9 on 2018-10-22
Does this help the new kernel to work properly?

```
echo deep | sudo tee /sys/power/mem_sleep
```

---

### Post by hackerb9 on 2018-10-22
By the way, there was some funkiness that happened in the kernel power management around 4.15. Trying 4.14 instead of 4.4 may be a good idea.

---

### Post by Ralph L on 2018-10-24
I'll try your suggestions, when I load a new system.  I don't want to disturb my current system, since it is working.

Thanks for your response.

---

### Post by Ralph L on 2018-11-12
hackerb9
I checked the contents of /sys/power/mem_sleep and found it to be: "s2idle [deep]".  This isn't exactly what you wanted me to put in there, but I think it accomplishes what you were suggesting.  Also, I loaded xubuntu 18.10, installed it, did the required software update, and using UKUU updated the kernel to 4.19.1.  This didn't fix any problems so I am going back to kernel 4.4.0.97 under xubuntu 18.04 LTS.  Everything seems to work fine with that setup.
Thanks for responding to me.

---

### Post by Ralph L on 2019-01-07
I did some further testing and found the Kernel 4.6.2 would work ok, but 4.6.3 would not work.  It gives errors during boot time, which Kernel 4.6.2 did not.  I am guessing that the boot errors cause the later suspend, shutdown problems.
By the way, does anybody know how to get the boot errors from a log someplace so that I can post them???  And maybe also the shutdown log, when the computer hangs on shutdown.

---

