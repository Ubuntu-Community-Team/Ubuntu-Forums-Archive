---
title: "Random crashes when streaming"
date: 2013-01-21
forum: General Help
---

### Post by d3ngar on 2013-01-21
Hi,

I am experiencing quite random crashes when I'm streaming either video or audio files through the browser. It isn't the whole system that crashes, it's actually only the display that stops. The audio generally keeps playing and even the mouse is still responsive. If I restart lightdm, everything works okay, but it's obviously pretty annoying.

The issue occurs in both firefox and chrome.

I can't seem to figure out what's wrong. Dmesg and also syslog don't really show any visible issues.

Is there something that I could do?

Thanks,

Chris

---

### Post by d3ngar on 2013-01-23
bump!

---

### Post by tgalati4 on 2013-01-23
What is your system?  CPU?  How fast is your internet connection?  It sounds like a bandwidth problem.  Can you run a commandline player like mplayer with a URL of a valid stream and see if it streams OK?

Also vlc has a console player called cvlc.  You can play a video from the console and you will get some error messages/dropped frames if your bandwidth is too low.

---

### Post by d3ngar on 2013-01-28
Bandwidth problem, really?

The system is a AMD Athlon 64 X2, 3000 Mhz. It has 1 GB of RAM DDR2 666 Mhz.

I will try using the commandline players for the URL and see if that makes any difference. 

If it is a bandwidth problem, it shouldn't really be able to affect the system as a whole. Why isn't anything at all responding?

---

### Post by tgalati4 on 2013-01-28
Open a terminal, install htop and monitor your I/O waits while streaming:

```
sudo apt-get install htop
htop
```

Control-C to quit htop.  I/O waits will cause a system to freeze--problems with a disk drive, cables, power supply, etc.  It's also possible that your southbridge also controls your ethernet connection and sound chip.  So streaming can cause a double load on the southbridge causing it to hang--more I/O waits.

---

### Post by d3ngar on 2013-02-07
I installed htop, but I'm afraid I don't know how I can see the I/O...

I also tried streaming through VLC, just a normal YouTube clip and I didn't see any issues.

The problem remains though and it is very frustrating. Because I have no TV, I watch everything streamed... now I have no things to watch :(.

Thanks for your help!

---

