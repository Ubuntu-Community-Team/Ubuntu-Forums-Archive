---
title: "gnome-terminal lag"
date: 2008-06-12
forum: General Help
---

### Post by nlarusso on 2008-06-12
After about 2 years of using my current system I've started to experience an odd occurrence. It seems that every couple of minutes my terminals become unresponsive for a period of time. If I have typed a command to the terminal, it will just sit - using what appears to be its normal share of cpu - for up to about a minute or two before executing the command.

I have tried multiple times to restart my system but that has not fixed the problem. I've upgraded gnome - also has not helped. 
I'm running Ubuntu 7.10

](*,)

Any suggestions would be great.

---

### Post by nlarusso on 2008-06-13
So it appears that the gnome-terminal is 'sleeping in' and thus commands issued through the terminal are not being executed until it wakes back up.

I also noticed that when I run commands in super-user mode they work fine (no delay). So as a temporary fix, I've increased my gnome-terminal niceness to give it a higher priority. This seems to be working thus far.

---

### Post by creatorbri on 2011-07-04
I'm having the same problem! It's tremendously frustrating, having to wait 30-60 seconds or so every few minutes for my terminal to start responding again. I tried switching to superuser mode, but no dice.

Anyone have any ideas??

EDIT: I'm on Ubuntu 10.04.

---

