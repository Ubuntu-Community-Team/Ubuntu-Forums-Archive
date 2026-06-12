---
title: "black screen after restart X"
date: 2007-11-16
forum: General Help
---

### Post by killerwhale65 on 2007-11-16
hi,

I had to restart X (ctrl-alt-backspace), but i never saw my desktop back, just a black screen. After A restart of the PC, still the black screen. What should i do?

thanks!

Matt

---

### Post by PmDematagoda on 2007-11-16
Go through Recovery Mode and then try this:-
```

dpkg-reconfigure -phigh xserver-xorg
```
and see if that solves your problem.

---

### Post by zeller on 2007-11-16
I've had the same problem. Be patient and maybe it will boot properly. It has taken my Gutsy about 4-5 minutes to boot up.

Sometimes I have to do a ctr+alt+del numerous times before it "just works."

Hopefully, someone with more knowledge can chime in.

---

### Post by killerwhale65 on 2007-11-16
i did that from terminal mode, but not in recovery mode. It didnt help. I will try in recovery mode (not sure if that matters).

---

### Post by zeller on 2007-11-16
> **PmDematagoda said:**
> Go through Recovery Mode and then try this:-
```

dpkg-reconfigure -phigh xserver-xorg
```
and see if that solves your problem.

Can you explain what that all means?

---

### Post by PmDematagoda on 2007-11-16
That option basically reconfigures the X-server to the default settings instead of "sudo dpkg-reconfigure xserver-xorg" which completely reconfigures the X-server.

And if the command didn't work in the normal mode, then it most probably will not work on Recovery Mode. Instead of that command then, could you use:-
```

sudo dpkg-reconfigure xserver-xorg
```
and then select the choices which you know are correct, after reconfiguration see if your problem is solved using:-
```

sudo startx 
```

Could you also post the specifications of your system?

---

### Post by zeller on 2007-11-16
Well, I have:

HP zd8000
3 Ghz Pentium 4 with HT
Broadcom wireless chipset

What else do you need?

---

### Post by PmDematagoda on 2007-11-17
According to this:-

[http://www.notebookreview.com/default.asp?newsID=2248&review=ZD8000](http://www.notebookreview.com/default.asp?newsID=2248&review=ZD8000)

you have an ATi card, I cannot help you much there as my expertise is with Nvidia cards, but you can give the command I previously gave you a try since you know that your VGA card does work on Ubuntu. I'm very sorry I cannot be of more assistance.

---

