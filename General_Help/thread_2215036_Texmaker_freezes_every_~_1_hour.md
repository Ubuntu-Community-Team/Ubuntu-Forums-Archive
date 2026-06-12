---
title: "Texmaker freezes every ~ 1 hour"
date: 2014-04-04
forum: General Help
---

### Post by childintime on 2014-04-04
So I was using Texmaker for quite some time and it always worked well, but now it is second day as every 1--2 hours it completely freezes at random time. Just mouse freezes in place, no keyboard commands work whatsoever, but music still plays if I have it running. But it freezes only when I am in Texmaker itself.

The only solution is to reboot or ALT+PRTSCR+REISUB.

---

### Post by tgalati4 on 2014-04-04
Look through the log files in /var/log, especially at the time of the freeze.

Run texmaker in a terminal and see if there are any error messages that come up.  Keep the terminal "Always on Top" so if it freezes you can at least see some messages.  Log in using ssh from another computer.  If it freezes, see if the other terminal on the other computer is responsive.  If so, then you can issue:

```
sudo shutdown -h now
```

To perform a clean shutdown.  

It's possible that you are having a graphics freeze.  Control-Alt-Backspace should allow you to reboot the graphics (if enabled).  Control-Alt-F1 or F2 or F3 or F4 should get you to a terminal where you can shutdown if the graphics are frozen but the system is still limping along.

It's possible that you have developed a hardware fault.  Are you writing a thesis that requires LaTex?  Computers tend to act up when you really need them.

Also, shut down all extraneous processes and services.  If you are streaming music, sometimes the southbridge chip that handles audio also handles ethernet and it will get hot and cause issues.  What is the model of computer?  eMachines is not a correct answer.

---

### Post by childintime on 2014-04-04
Hey, thanks for response.

I've got Asus K56C laptop. I use LaTex to write kinds of university work, and now it's first time it started to act weirdly. Alright, I will try some stuff you told, but since it's freezes at random times it's hard to troubleshoot.

---

