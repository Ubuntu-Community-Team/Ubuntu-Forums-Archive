---
title: "Both CPUs in system monitor are jumping around alot."
date: 2008-06-28
forum: General Help
---

### Post by siefer7 on 2008-06-28
In the system monitor both my CPUs randomly jump from a full load then to 10%ish, then back to %100. They just alternate. And both are never really all the way down to zero, usally around 10% most of the time, even without doing anything. I'm used to in windows when i don't move it goes down to zero. Is this normal at all? At least for it never going to zero? 

Also the last 2 times i had system monitor open, if i had firefox open, eventually it would just all dim/desaturate and then it wouldn't respond. Just the firefox window.

I have a custom pc with a EVGA 680i SLI MB, E6850 Core 2 duo, 8 Gig RAM, EVGA 8800 Ultra. Running Ubuntu Hardy 64, dual booted with xp 64 bit.

if there is any more information to provide that would help just let me know.

I greatly appreciate any help. 

Thanks :)

---

### Post by sdennie on 2008-06-28
If you are basing this information on the gnome panel applet that shows CPU speed, it won't be accurate.  It shows the information at the moment that it polls it and so doesn't show the overall CPU state.  I recommend using powertop:

```

sudo apt-get install powertop
sudo powertop

```

That should give you a better idea of what you CPU is doing.

---

### Post by Winawer on 2008-06-28
As a response to whether or not continual, sporadic CPU activity is normal, in general the answer is "yes".  There are a lot of processes in the background of your system (opening a terminal window and entering the command "top" will give you an idea of what's going on), and this is a normal part of computing.  Whether or not there are unwanted processes running is a different story, though.  Use top or ps (or the gnome system monitor) to see what's running if you're concerned.

And as to why both CPUs are lighting up, it's probably a function of the kernel scheduling processes.  As an extreme example, if one processor has a task running and a second is lying idle, the kernel will throw any new tasks onto the second processor to maximize system response - at least, as far as I know;  I'm not a kernel hacker, so I may have some of the details wrong.

Hope that helps!

---

