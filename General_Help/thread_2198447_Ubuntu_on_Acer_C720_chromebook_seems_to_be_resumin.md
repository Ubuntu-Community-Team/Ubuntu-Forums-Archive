---
title: "Ubuntu on Acer C720 chromebook seems to be resuming from suspend while in my bag"
date: 2014-01-08
forum: General Help
---

### Post by Stratosmacker on 2014-01-08
Today is the first day back at uni, and I brought along my newly acquired c720 to do work on. I noticed that when I first opened it in my first class, the battery was at 85% and seemed to have been discharging for about 1.5 hrs (how long it had been since I had unplugged it). I didn't have problems until I closed it after my last class. Upon opening it ten minutes ago, it was without a charge, and sure enough, it seems to have turned back on between classes. Here are two interesting excerpts from pm-suspend.log:

Output:

jesse@jesse-Peppy:~$ cat /var/log/pm-suspend.log | grep -i "performing suspend"
Thu Jan  2 01:36:40 EST 2014: performing suspend
Wed Jan  8 01:58:27 EST 2014: performing suspend
Wed Jan  8 02:55:36 EST 2014: performing suspend
Wed Jan  8 10:13:18 EST 2014: performing suspend
Wed Jan  8 10:50:43 EST 2014: performing suspend
Wed Jan  8 12:06:43 EST 2014: performing suspend
Wed Jan  8 12:07:21 EST 2014: performing suspend
Wed Jan  8 12:55:11 EST 2014: performing suspend
Wed Jan  8 15:15:41 EST 2014: performing suspend
Wed Jan  8 15:42:00 EST 2014: performing suspend
Wed Jan  8 15:47:23 EST 2014: performing suspend
Wed Jan  8 15:52:44 EST 2014: performing suspend
Wed Jan  8 15:58:06 EST 2014: performing suspend
jesse@jesse-Peppy:~$ cat /var/log/pm-suspend.log | grep -i "Awake"
Thu Jan  2 01:36:46 EST 2014: Awake.
Wed Jan  8 02:37:28 EST 2014: Awake.
Wed Jan  8 02:55:56 EST 2014: Awake.
Wed Jan  8 10:13:38 EST 2014: Awake.
Wed Jan  8 10:51:03 EST 2014: Awake.
Wed Jan  8 12:07:03 EST 2014: Awake.
Wed Jan  8 12:07:41 EST 2014: Awake.
Wed Jan  8 12:55:31 EST 2014: Awake.
Wed Jan  8 15:40:22 EST 2014: Awake.
Wed Jan  8 15:42:20 EST 2014: Awake.
Wed Jan  8 15:47:43 EST 2014: Awake.
Wed Jan  8 15:53:04 EST 2014: Awake.
Wed Jan  8 15:58:26 EST 2014: Awake.


I got out of class at about 15:45. The five min interval suspend before that was because of the "suspend after 5 min inactivity" setting I had put on briefly. Everything after that was on the laptop's own. I have used this for a few weeks, very casually at home, and have not noticed this. I also haven't been caring it around in a bag.

Is there any way I can see *why* the laptop suspended, and not just when? I know you can see this on a Mac with a look through the output of syslog, but I can seem to find anything on linux

Thanks!!

---

### Post by Stratosmacker on 2014-01-08
Upon further research, the pattern seems to be that I can not suspend TWICE since a poweron. Suspend once it works fine, supend twice, and it dips into sleep for about a second and wakes back up. I am using some strange kernel flags for compatibility, and maybe that has something to do with it? my grub file reads: 

GRUB_CMDLINE_LINUX_DEFAULT="add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic"

that is from the link on this thread: [http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/](http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/) or [https://plus.google.com/+PedroLarroy/posts/6CgQypQukMa](https://plus.google.com/+PedroLarroy/posts/6CgQypQukMa)

---

### Post by Stratosmacker on 2014-01-08
AHH and when shutting down after a supend having happened, this is thrown:
ehci-pci 0000:00:1d.0: port 1 resume error -19

which is:
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)

That's where I'm lost. Apparently this is some sort of intel powersaving chipset? It seems that after suspend, something breaks which keeps the computer on and causes me problems

---

### Post by TheFu on 2014-03-23
Did this get solved? 

I'm interested in completely disabling the POWER button, if possible.
As a touch typists, I keep hitting it, since that is where the DELETE key belongs. If it just suspended, that wouldn't be as bad as what happens currently - powering off.  Attempts to remap this key have failed.  F10 and all other key remappings are working nicely.

I've modified the  /etc/systemd/logind.conf - but that doesn't seem to matter.

**sudo pm-suspend** does work, at least the first time.

---

