---
title: "Could kernel update have broken firmware loader?"
date: 2007-03-07
forum: General Help
---

### Post by r76 on 2007-03-07
I have been running Ubuntu Edgy since October last year.  I mostly use it for recording TV programs, editing them and burning to DVD - to view and record TV from my USB Artec T1 DVB box I use Kaffeine 0.8.2, as in [_this thread_]("http://www.ubuntuforums.org/showthread.php?t=241650&page=2")

This worked fine for months, as Kaffeine automatically recognised this box (did not work without tweaking in Dapper) because the firmware is correctly loaded when plugged in.  However I recently updated Ubuntu through the security updates pop-up that appears in the sytem tray, and now Kaffeine no longer detects the box, i.e. in the initial menu of Kaffeine, the Digital TV icon does not appear - this is exactly the same effect as I get when I start Kaffeine without the DVB box plugged in.

What concerns me is could a kernel update have caused the breakage?  I now have two extra options in my boot manager - there is now:
2.6.17.11
2.6.17.11 (recovery mode)
2.6.17.10
2.6.17.10 (recovery mode)
Windows XP

The default has become 2.6.17.11 (this wasn't there before), but if I scroll down to 2.6.17.10 my setup works perfectly as it did before.  If it is a kernel update that broke my set up, how do I
1) let the people who made the kernel know about this
2) revert to my previous kernel

If I remove the faulty kernel will my system be vulnerable? I also use it for internet access.
Thanks for any help!

---

### Post by Kateikyoushi on 2007-03-07
No, your PC is not more vulnerable if you stick with the old kernel.
Concerning the kernel you could write a bugreport on launchpad but make sure first that you load the module and it matches the kernel.

---

