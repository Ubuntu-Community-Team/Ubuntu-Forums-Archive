---
title: "hardy heron screen blacks out unresponsive"
date: 2008-04-28
forum: General Help
---

### Post by Saghaulor on 2008-04-28
After a certain amount of time my screen blacks out. I try to hit several keys, including enter, esc, cntl alt del, nothing changes it. It is just a blank unresponsive screen. I turned off the screen saver, and it still does this. I have to hard reboot in order for it to do anything.

Any ideas?

---

### Post by amohanty on 2008-04-29
does a ctrl+alt+backspace help?
it restarts the x server.

am

---

### Post by Saghaulor on 2008-05-20
> **amohanty said:**
> does a ctrl+alt+backspace help?
it restarts the x server.

am

The X server restarts, but then all of my open applications are closed.

Any other ideas?

---

### Post by llama320 on 2008-05-20
I had the same problem. First of all, can you access your virtual terminals (ctrl-alt-F#)?

If you get just a blank screen where your virtual terminals should be, then it's probably a problem with the nvidia driver (assuming you're using nvidia..)

Now, I'm also assuming you're using nvidia-glx-new as the driver right now. If you don't care about compiz working, then nvidia-glx will probably remedy this problem.

To get compiz working, though, what I had to do was manually install nvidia driver 100.14.23..it's pretty old but it works

here's the thread I made for this problem, hope it helps
[http://ubuntuforums.org/showthread.php?t=780996](http://ubuntuforums.org/showthread.php?t=780996)

If you don't want to get that involved, and you just need to get out of the sleeping-screen-thinger, all I had to do was press Ctrl+Alt+F1, then wait a second or two, then Ctrl+Alt+F7 to bring X back, and ta-da

Good Luck

---

