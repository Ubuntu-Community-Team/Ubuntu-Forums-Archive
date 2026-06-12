---
title: "Keyboard randomly stops working, need script"
date: 2015-12-29
forum: General Help
---

### Post by coldraven on 2015-12-29
Hi, I'm running 64 bit Ubuntu 15.10 on a dual core laptop.
My keyboard randomly stops working but it can be re-started by logging out and logging back in.
What I need is a script that is clickable that will re-start the keyboard, obviously I cannot even open a terminal with Ctrl+Alt+T to run a script when this happens.
Any suggestions greatly welcomed.

---

### Post by DuckHook on 2015-12-29
My system works with two keyboards (1: USB, 2: PS/2) but generates a flood of interrupts to the log from the PS/2, so I've unplugged that one. But you may wish to try plugging in two keyboards to see if one is still available when the other freezes. Also, set up ssh on the laptop to allow you another entry option.

To chase down the problem, what do *dmesg* and *syslog* say?

---

### Post by coldraven on 2015-12-30
> To chase down the problem, what do *dmesg* and *syslog* say?
Of course now I try to fix it the problem has not happened today so far. I'll get back to you the next time it conks out.

---

### Post by DuckHook on 2015-12-30
BTW, re: title, I don't know of any script that could handle a problem such as yours. How would the system sense that the keyboard had stopped working? Keyboards are always simply waiting for input that, in your case, never comes. I don't see what kind of script logic would allow for response to something inherently unpredictable.

I would note that I tinker with a lot of old equipment, and whenever I experience intermittent and patternless failures of any kind, I suspect physical or mechanical causes. Check your keyboard itself, experiment with a different one, change USB ports, is the keyboard cord kinked or frayed, etc. It's embarrassing how much time I've spent chasing OS and software ghosts when the problem was a failing HDD, bad memory module, or cracked motherboard.

<EDIT>

My bad. After re-reading your post, the mouse obviously still works, so you wanted a script that you could invoke with the mouse. Sorry. Forgot to take my smart pills this morning.

<FURTHER EDIT>

Further thought: do you use a wireless keyboard? I do, and sometimes, the keyboard just drops its connection to its wireless transmitter. I then have to pop out the keyboard batteries and pop them back in again. This resets the connection and, presto, I'm back in business. It's irritating, but only happens once every couple of months or so. More frequently as the batteries run down. Should have occurred to me to ask you this first. <sigh> Am I slow today or what?

---

### Post by coldraven on 2015-12-31
I suppose that what I wanted was a script that restarts the X-system or whatever it is that happens when you log out and then back in. Making it into a launcher icon would enable me to click it.
However, and most strangely, the problem has not so far recurred. This is a laptop with inbuilt keyboard. What I don't know is if this is a hardware problem or an ancient bug. After a clean install of 15.10 the keyboard kept reverting to US rather than UK configuration. I was the 100th. person to report this bug. So it's a bit of a mystery!
Anyway this can wait, have a Happy New Year! <me goes off to pub> :)

---

### Post by leunam12 on 2015-12-31
make a script like this :
```
#!/bin/bash
#This script will restart the desktop environment.
sudo restart lightdm

```

make it executable.
```
chmod +x myscript.sh
```

Add it to your sudoers file
```
sudo visudo
```

something like this

```
username ALL=(ALL) NOPASSWD: /sbin/restart lightdm
```
to run it just double-click it, if there is a prompt choose 'Run'

I think that should do it. Let's see if someone with more experience has an easier way or catches a bug in my code.

---

