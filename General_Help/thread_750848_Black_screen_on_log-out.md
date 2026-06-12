---
title: "Black screen on log-out"
date: 2008-04-09
forum: General Help
---

### Post by AdrianStrays on 2008-04-09
If I attempt to change users by means of the "log-out" function, I receive a black screen, and have to turn my computer off with the power button.  Any help?

In a related note, what damage does press the power button do in Linux? I know it causes problems in Windows, but how about Ubuntu?

---

### Post by simonn on 2008-04-10
"what damage does press the power button do in Linux? I know it causes problems in Windows, but how about Ubuntu?"

Similar to windows, i.e. there is the potential to lose data etc. However, if you are using a journaled file system (e.g. ext3 which is the default for ubuntu) it is unlikely that the file system will get corrupted, unlike windows.

Back to the problem...

When you have the blank screen, can you press ctrl + alt + F1 (or F2 to F6) and get a terminal log in screen?

If you can then the X server has not crashed, so log in and check the most recent xorg log by running the command (note: do not type the $ that represents the prompt, by convention $ = run as your normal user # = run as root):

```

$ cat /var/log/Xorg.0.log

```

Do you see any errors or exceptions etc? Post the contents of the file here if you need to.

What video card do you have?

I had what sounds like the same or a similar problem this week when I upgraded to Hardy (beta). I have an nvidia FX5200 and the latest nvidia drivers (169.12) were causing the PC to crash when the X server was restarted (e.g. when logging out, sudo /etc/init.d/gdm restart etc). There was nothing in any logs either. So, I downgraded the nvidia drivers (to 100.14.19) which fixed it.

---

