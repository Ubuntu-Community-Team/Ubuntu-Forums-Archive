---
title: "Kernel panic + drop_buffers = serious problem??"
date: 2008-04-15
forum: General Help
---

### Post by Big_J on 2008-04-15
The problem started about three days ago, my main Desktop started to freeze. Everything just freezes, including mouse, and I cannot switch to other shells or restart x, the only thing I can do is hard reset. 
After the first time it happened, it happened at random, at the login window, five minutes after login, an hour after login, can't predict it. About 20% of these freezes, the caps lock and scroll lock LEDs started flashing, which I understand is a sign of a Kernel Panic...

So this happened about ~22 times, and fsck started automatically. 
fsck runs for a little bit, then it goes like this:
```
[    92.459964] Call Trace:
[    92.460078]  [<c01a1566>]  try_to_free_buffers+0x36/0x90
[    92.46xxxx]  [<c01xxxxx>] shrink_inactive_list+0x765/0x8a0
and a bunch more status messags

```
And then the last line:
EIP: [<c01a145d>] drop_buffers+0x1d/0xf0 SS:ESP 0068:df85fddc

and freezes. Does that mean that I have a bad harddrive sector or something? How do I fix this problem, please help as I need this computer for work.
I didn't copy all the text, because I don't know where the log file is located so I'm typing everything in, so if you need to see all the numbers, please let me know where the log file is... 

Please help. I tried googleing to no avail, I usually solve all my problems, but no one seems to have experienced something like this before... 

System:
AMD Sempron
7800rpm 250GB Caviar HDD
2GB pc3200 ddr ram
nVidia geforce

I've had this same setup for over three years, and used multiple versions of ubuntu with no problems, the last time I upgraded ubuntu was ~six months ago with the last release. No hardware modifications. The last thing I did before the first freeze was open a torrent and start to download a file, if that helps.

Edit: I can't start in failsafe mode either, as it also starts fsck and the computer won't start. Please help!

---

### Post by Big_J on 2008-04-15
Started ubuntu with an older kernel, fsck finished this time. 
It outputed something, but I didn't catch it all because it restarted. All I saw was a red "ERROR" on the right of the screen, and ***RESTART LINUX***
There was a few more lines of text, and then the computer rebooted, this time I was able to login, I don't know if anything was fixed, I'll have to see if it crashes again. Please help if you know anything about this!

---

### Post by Big_J on 2008-04-16
Yup, froze again, another kernel panic. 
Anyone? Please help!

---

### Post by Big_J on 2008-04-20
Comon... No replies at all? 
No one is willing to help me on this??
Please help!

---

### Post by Big_J on 2008-04-20
I think I got it, it's a bad stick of ram..
Though I wonder why no one was willing to help? I remember when I first started using ubuntu, everyone used to reply to help topics right away, and now you leave a serious problem that dissabled my main desktop go ignored!
What happened here?

---

