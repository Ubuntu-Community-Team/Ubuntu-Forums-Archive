---
title: "Terminal shutdown needs admin access. Why?!"
date: 2006-08-07
forum: General Help
---

### Post by Mr. Picklesworth on 2006-08-07
I found a thread in the 5.10 forums which explains how to allow any user to run the Poweroff or Shutdown command without needing a password, but I find the whole situation really inconsistent.

Why do I have to mess around with Sudo stuff in order to shutdown the computer via the terminal when I can do it via the visual desktop environment without having to enter an admin password?

It would make sense to block Poweroff for remote users by default, but for a local user it makes no sense, especially when I could do far more damage by unplugging the computer.


This bothers me because, just recently, I went away for a week but needed to send a file to someone when I was not home.
The solution was quite wonderfully simple: sleep 12h;poweroff
I've used Poweroff before, and at the time I never really thought much about needing Sudo for it.
So this time, I came home to find that my computer had not shut down and instead told me that to shut it down I need to run the program with Sudo.

Is there a command hidden away somewhere that turns off the computer as pleasantly as going to System -> Quit in the menu?

Err... I think I have a few questions in there. Sorry about the rambling :oops:
Thanks in advance!

---

