---
title: "Terminal Text at Startup"
date: 2014-04-10
forum: General Help
---

### Post by Kyle_Undercofler on 2014-04-10
Sometimes, when I reboot my computer, it sucks me away to a black screen with a bunch of white text :( . Thankfully, I can boot my computer properly after some messing around with the options in the recovery mode menu :) . Next time it happens, I'll take a picture of my screen. It's not that big of a problem, it's just confusing :confused: , and I want to know what it means.

---

### Post by Double.J on 2014-04-10
Hi there!

hmm, can be a couple of things obviously!

It could well be busybox prompt? Does that sound familiar?
Also do you get any other errors during boot, such as 'cannot find swap' or the 'keep waiting?' Question?

Jj

---

### Post by Kyle_Undercofler on 2014-04-10
Never heard of busybox. When it happens I see things like "watchdog" and "nosemaphore". Also, I can't do anything when it happens. As I said though, it's not that big of a problem. Next time I reboot my computer and get the error I'll post a picture.

---

### Post by grahammechanical on 2014-04-10
Ubuntu runs on top of Linux. What you are seeing is Linux messages as Linux loads. These are usually hidden by a splash screen. But something is happening to your system. 

Watchdog

[http://linux.die.net/man/8/watchdog](http://linux.die.net/man/8/watchdog)

Semaphores

[http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html](http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html)

[http://www.linuxmanpages.com/man3/sem_init.3thr.php](http://www.linuxmanpages.com/man3/sem_init.3thr.php)

I do not understand what all that says but I guess that no semaphores is not a good thing. Start backing up your data. A re-install may be needed one day.

Regards.

---

### Post by Kyle_Undercofler on 2014-04-12
> **grahammechanical said:**
> Ubuntu runs on top of Linux. What you are seeing is Linux messages as Linux loads. These are usually hidden by a splash screen. But something is happening to your system. 

Watchdog

[http://linux.die.net/man/8/watchdog](http://linux.die.net/man/8/watchdog)

Semaphores

[http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html](http://www.linuxdevcenter.com/pub/a/linux/2007/05/24/semaphores-in-linux.html)

[http://www.linuxmanpages.com/man3/sem_init.3thr.php](http://www.linuxmanpages.com/man3/sem_init.3thr.php)

I do not understand what all that says but I guess that no semaphores is not a good thing. Start backing up your data. A re-install may be needed one day.

Regards.

Huh. Funny thing is, I was having the same problem a while ago, so I re-installed, but it's still happening. Thankfully, not as often though.

---

