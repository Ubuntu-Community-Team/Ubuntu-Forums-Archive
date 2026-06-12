---
title: "imwheel gets XError: BadAccess when trying to run on 22.04"
date: 2022-06-22
forum: General Help
---

### Post by zzarko on 2022-06-22
A few days ago I finally installed 22.04, Mate version, and started to re-install all that I need. One of things is imwheel, for tweaking how internet browsers are used. I copied my settings from old installation (.imwheelrc) and tried to run the program. Since it did not work, I tried debug option and got this at the end of printout:
```
Grabbing Button 8...
Grabbing Button 9...
starting loop...
XError: 
    serial      : 12
    error_code  : 10
    request_code: 28
    minor_code  : 0
    resourceid  : 1753
    error string: BadAccess (attempt to access private resource denied)
XError: 
    serial      : 13
    error_code  : 10
    request_code: 28
    minor_code  : 0
    resourceid  : 1753
    error string: BadAccess (attempt to access private resource denied)
```
Now, I do not mind getting dirty and solving problems on my own, but this one left me without a solution. All that I could find regarding this BadAccess error was related to various Qt programs and solutions offered on pages that I found cannot be applied. I also found one advice for moving start of imwheel into systemd service, but that one had the same error in the end.

So, now I have no idea whatsoever as to where to look for solution, as I have no idea what that error means and where to even start to find a solution. All I figured out is that imwheel needs access to something that was freely accessible in 18.04, but now it isn't. Does anyone has any idea as to what is wrong/changed and how to solve it?

---

### Post by tbird761 on 2022-07-10
I ran into the same issue on Debian just today.  I'd been running a perpetually upgraded installation started in 2018.  In my case, I found no solutions other than testing if it ran as root.  It did.  I killed the daemon and restarted it as my regular user after that, and suddenly it decided it wanted to work fine.  Running the process successfully once must have helped in some manner.

---

