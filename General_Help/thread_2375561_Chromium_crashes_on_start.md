---
title: "Chromium crashes on start"
date: 2017-10-25
forum: General Help
---

### Post by simonhk2 on 2017-10-25
Hi

I suddenly started having a problem with Chromium a while ago, it just died and whenever I try to restart it, it instantly crashes again.
I've tried to remove Chromium and everything associated with it, then installed it again but it makes no difference.

I've also tried to run chromium-browser --temp-profile which starts up Chromium as expected, but after using it for a very short time it just dies again.

Any ideas what is wrong or what to do?
Thanks!

Attempting to run Chromium produces the following output that I can't make any sense of:
```

Received signal 11 SEGV_MAPERR 000000000010
#0 0x7fdd4f1fd0c6 base::debug::StackTrace::StackTrace()
#1 0x7fdd4f1fd4ab <unknown>
#2 0x7fdd4f52a630 <unknown>
#3 0x55f72eccefd8 <unknown>
#4 0x55f72ecd1866 <unknown>
#5 0x55f72ecd200e <unknown>
#6 0x55f72ecd233f <unknown>
#7 0x7fdd4f27a831 <unknown>
#8 0x7fdd4f1feb4a base::debug::TaskAnnotator::RunTask()
#9 0x7fdd4f2291e0 base::MessageLoop::RunTask()
#10 0x7fdd4f22ac9d base::MessageLoop::DeferOrRunPendingTask()
#11 0x7fdd4f22bb3d <unknown>
#12 0x7fdd4f22c612 base::MessagePumpLibevent::Run()
#13 0x7fdd4f228235 base::MessageLoop::RunHandler()
#14 0x7fdd4f252ef8 base::RunLoop::Run()
#15 0x7fdd4f27fdc6 base::Thread::ThreadMain()
#16 0x7fdd4f27a6b6 <unknown>
#17 0x7fdd4f5206ca start_thread
#18 0x7fdd38ca5caf clone
  r8: 0000000000000001  r9: 000055f73078d3ac r10: 000055f73078d3b0 r11: 00007fdd38d30330
 r12: 00007fdca3ffcfb0 r13: 0000000000000008 r14: 0000000000000008 r15: 00007fdca3ffce70
  di: 0000000000000000  si: 00007fdca3ffce70  bp: 00007fdca3ffcec0  bx: 00007fdca3ffce70
  dx: 00007fdc8400a1a0  ax: 0000000000000000  cx: 0000000044495547  sp: 00007fdca3ffce20
  ip: 000055f72eccefd8 efl: 0000000000010202 cgf: 002b000000000033 erf: 0000000000000004
 trp: 000000000000000e msk: 0000000000000000 cr2: 0000000000000010
[end of stack trace]
Calling _exit(1). Core file will not be generated.
```

---

### Post by vasa1 on 2017-10-25
Where did you get```
--temp-profile
```from?

I can't find that in [List of Chromium Command Line Switches]("https://peter.sh/experiments/chromium-command-line-switches/").

And what's your version of chromium-browser (and distro)?

---

### Post by simonhk2 on 2017-10-25
Not sure where I got that from, found it when trying to google the issue and someone suggested that as a workaround. Not really relevant as it doesn't help much except keep the browser alive for 30 or so seconds instead of instantly crashing.

Distro is Lubuntu.
Chromium 59.0.3071.109 Built on Ubuntu , running on Ubuntu 16.10

---

### Post by ajgreeny on 2017-10-25
Lubuntu 16.10 along with all the other *ubuntu 16.10 varieties is now out of support so you should update to one of the supported versions to avoid security risks; at present I would suggest 16.04 or 17.10 until next April when the next LTS version will appear, ie 18.04.

For your particular problem I suggest you try renaming the hidden configuration folder in your home at **~/.config/chromium** and see if that helps; if so it means your current profile is at fault.

For your info, the current chromium is version 61.0.3163.100 which you do not have as the repos for 16.10 are now closed to any new packages.

---

### Post by simonhk2 on 2017-10-26
> **ajgreeny said:**
> Lubuntu 16.10 along with all the other *ubuntu 16.10 varieties is now out of support so you should update to one of the supported versions to avoid security risks; at present I would suggest 16.04 or 17.10 until next April when the next LTS version will appear, ie 18.04.  For your particular problem I suggest you try renaming the hidden configuration folder in your home at **~/.config/chromium** and see if that helps; if so it means your current profile is at fault.  For your info, the current chromium is version 61.0.3163.100 which you do not have as the repos for 16.10 are now closed to any new packages.  Thank you!  I've got no clue how I ended up with a non-LTS, that was never the plan, hmmm...  Guess I will have to figure out how to upgrade and hope it solves the problem.

---

