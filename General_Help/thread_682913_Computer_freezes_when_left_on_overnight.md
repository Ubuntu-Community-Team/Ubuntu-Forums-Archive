---
title: "Computer freezes when left on overnight"
date: 2008-01-30
forum: General Help
---

### Post by Rahu on 2008-01-30
No idea what the problem could be here. I had previously been using ubuntu on this exact computer for many months with no problem.

Whenever I leave the computer on overnight(or any long amount of time I would assume) the keyboard stops responding(but num/caps lock lights stay on, so it's working a little at least)  and I can't click on anything, though the mouse does move.

I've turned off all power-saving/screensaver stuff to make sure that wasn't interfering somehow, but it hasn't helped.

Any ideas on what could be causing this?

---

### Post by Het Irv on 2008-01-30
Is the computer trying to hibernate or go into suspend mode and then stopping in the middle of the process?

---

### Post by Rahu on 2008-01-30
Nope, I've turned off everything related to power saving that I could find.

It also just happened again when it had been about an hour since I last used the computer, so I don't think it has to do with idle time.

Seems like a hard lock of X, ctrl+alt+backspace does nothing, but like I said, the mouse moves around perfectly, its just that clicking doesn't do anything.

---

### Post by Het Irv on 2008-01-31
One soution might be to reinstall Ubuntu, your X Server might have gotten corrupted.  Look at the QuickStart link in my sig if you are going to reinstall I will save you some time, although I would not back up your configuration files, or anything related to X Server.

---

### Post by dabl on 2008-01-31
Open a console window and run```
 top
```

Move it down in the corner of your screen and let it run.  It always shows the running processes in descending order of CPU usage.  So, when your machine appears to be "frozen" (which it really isn't), look at top and see which process is the bad boy that is hogging all the resources.

Also, to shut down your machine when it seems to be "frozen", do this:  Press and hold down the Ctrl and SysRq (aka "Print Screen") keys, and while holding them down press, in sequence, R, S, E, I, U, and B.  This will do a graceful shutdown/restart and help prevent filesystem (i.e. data) corruption.  :)

---

### Post by philinux on 2008-01-31
> **dabl said:**
> Open a console window and run```
 top
```

Move it down in the corner of your screen and let it run.  It always shows the running processes in descending order of CPU usage.  So, when your machine appears to be "frozen" (which it really isn't), look at top and see which process is the bad boy that is hogging all the resources.

Also, to shut down your machine when it seems to be "frozen", do this:  Press and hold down the Ctrl and Alt keys, and while holding them down press, in sequence, R, S, E, I, U, and B.  This will do a graceful shutdown/restart and help prevent filesystem (i.e. data) corruption.  :)

I think you're right about the graceful shutdown but its the Alt Sysreq  to hold down. Best done with the pinkies I find.

---

### Post by dabl on 2008-01-31
Wow you are so right -- what a "senior moment"!  It's fixed -- thanks.  :popcorn:

---

