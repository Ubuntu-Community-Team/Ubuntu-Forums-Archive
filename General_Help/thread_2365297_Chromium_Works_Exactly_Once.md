---
title: "Chromium Works Exactly Once"
date: 2017-07-04
forum: General Help
---

### Post by daveculp on 2017-07-04
Brand new Install of 16.04.02, updated upon first boot.  I installed Chromium via the command line and it worked fine.  However, after exiting Chromium it would not restart.  The following is the output:

```
dwculp@darkstar:~$ chromium-browser 
Received signal 11 SEGV_MAPERR 000000000010
#0 0x7f937399f425 base::debug::StackTrace::StackTrace()
#1 0x7f937399f80b <unknown>
#2 0x7f9373cca390 <unknown>
#3 0x5630c965edc8 <unknown>
#4 0x5630c9661656 <unknown>
#5 0x5630c9661df9 <unknown>
#6 0x5630c9662143 <unknown>
#7 0x7f9373a1a821 <unknown>
#8 0x7f93739a0eea base::debug::TaskAnnotator::RunTask()
#9 0x7f93739c9e90 base::MessageLoop::RunTask()
#10 0x7f93739cb97d base::MessageLoop::DeferOrRunPendingTask()
#11 0x7f93739cc83d <unknown>
#12 0x7f93739cd300 base::MessagePumpLibevent::Run()
#13 0x7f93739c8f15 base::MessageLoop::RunHandler()
#14 0x7f93739f3628 base::RunLoop::Run()
#15 0x7f9373a1fe36 base::Thread::ThreadMain()
#16 0x7f9373a1a726 <unknown>
#17 0x7f9373cc06ba start_thread
#18 0x7f935d36f3dd clone
  r8: 000000000000002e  r9: 00005630cb0b56ec r10: 0000000000000000 r11: 00007f935d3fcf50
 r12: 00007f92c23efff0 r13: 0000000000000008 r14: 0000000000000008 r15: 00007f92c23efeb0
  di: 0000000000000000  si: 00007f92c23efeb0  bp: 00007f92c23eff00  bx: 00007f92c23efeb0
  dx: 000000000000005e  ax: 0000000000000000  cx: 00007f92940082e0  sp: 00007f92c23efe60
  ip: 00005630c965edc8 efl: 0000000000010206 cgf: 002b000000000033 erf: 0000000000000004
 trp: 000000000000000e msk: 0000000000000000 cr2: 0000000000000010
[end of stack trace]
Calling _exit(1). Core file will not be generated.
```

I deleted Chromium and reinstalled and got the same behavior, it would work once.  Rebooting did no good.  I had done some configuring and installing of other software prior to installing Chromium and so decided to wipe and reinstall.  I get the same behavior with the same error message output.   Any ideas?

---

### Post by CatKiller on 2017-07-05
So it looks like it crashes on exit? Is there still a zombie process listed in ps ax? If there is, can you relaunch Chromium after you've killed that process?

---

### Post by ajgreeny on 2017-07-05
I would start by renaming the hidden folder **~/.config/chromium** and see if that helps.

---

### Post by vasa1 on 2017-07-05
Related: [https://askubuntu.com/questions/932016/chromium-crashes-as-soon-as-i-log-in](https://askubuntu.com/questions/932016/chromium-crashes-as-soon-as-i-log-in)> So I deleted ~/.config/chromium and re-ran, and the browser didn't crash. Yay! but then I logged into Google, and crashed with the same message shown above. So I started it up again, and didn't log in. So far so good. But as soon as any complicated website is opened, it crashes within a few seconds.


And: [https://askubuntu.com/questions/931978/chromium-immediate-shutdown-upon-launch-ubuntu-16-04](https://askubuntu.com/questions/931978/chromium-immediate-shutdown-upon-launch-ubuntu-16-04)

---

### Post by daveculp on 2017-07-05
> **vasa1 said:**
> Related: [https://askubuntu.com/questions/932016/chromium-crashes-as-soon-as-i-log-in](https://askubuntu.com/questions/932016/chromium-crashes-as-soon-as-i-log-in) 

Thanks! This is the exact issue I am having.  I was able to fix it by disabling hardware acceleration and at least right now it appears to work.

---

### Post by ajgreeny on 2017-07-05
Great news! 

Please mark as **SOLVED** from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

