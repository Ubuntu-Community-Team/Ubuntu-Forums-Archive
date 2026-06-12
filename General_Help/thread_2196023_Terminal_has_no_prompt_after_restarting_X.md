---
title: "Terminal has no prompt after restarting X"
date: 2013-12-27
forum: General Help
---

### Post by ctbear on 2013-12-27
My ubuntu 12.04 LTS installation has gone weird this morning.
I got a new mouse plugged in to the computer, and I wanted to map some of the keys to certain functions (back, forward, etc). After reading some articles I made some modifications to xorg.conf, restarted the X server, and was stuck at a black screen at boot. After some scrambling I had to go to recovery mode, removed the xorg.conf changes, and it finally booted fine.
But now I have lost the prompt to the terminal. By that I mean when the terminal starts up, I can see a blinking cursor and it accepts keyboard inputs, but I don't see the actual prompt ($) and it doesn't do anything to the inputs. This is the same for gnome-terminal, xterm, uxterm, and the virtual terminal (Ctrl Alt F2).
One thing I notice is after a few minutes, the computer will slow down to a crawl and I can see the hard disk light flashing like crazy. The only way to get out of it is to reboot. It doesn't happen if I don't attempt to start the terminal at all.
Any advice on how I can troubleshoot it? This is a work computer so I would rather not reinstall the whole thing.

---

### Post by Impavidus on 2013-12-27
This sounds like there is some process in your .bashrc that never returns and slowly eats all memory on your computer. The disk light indicates your computer uses swap space. You only get a prompt once the last process in your .bashrc has returned.

Check the contents of your .bashrc. In principle, the problem can also be in your .profile or in /etc/profile or /etc/bash.bashrc. There must be a process never returning and using a lot of memory.

Does the problem exist when you use the guest login?

BTW, killing the terminal should help. I don't think you need to reboot when the problem occurs.

---

### Post by ctbear on 2013-12-27
I use zsh as my default shell, and after digging through my .zshrc I found the culprit to be the oh-my-zsh plugin. I guess I'll have to disable it for now.
Thanks for the help!

---

