---
title: "System is very frequently halted!!!"
date: 2008-04-18
forum: General Help
---

### Post by sfeone on 2008-04-18
Hi.

I once was a big Slackware user and now get more interested with this nice distribution, Ubuntu.

Unfortunately, I have a big problem. I installed the Ubuntu on my desktop (Dell XPS 410) and notebook (HP DV9429US). To get the network device on my laptop, I needed to get much help from other Ubuntu user. Finally, I could get it. 

Still, my big concern is that both systems used to be frequently halted with no explicit reasons. It happens at anytime. When I am watching movies, using VirtualBox, or even doing nothing, either system would halt. Since I am not a power user, I could not find the exact reason for this problem so that I do not know what I have to check on my system. Of course, I don't know if this is due to the bug of Ubuntu.

Please let me help for this problem.

Thank you so much.

---

### Post by ramjet_1953 on 2008-04-18
Probably the best way to attack this is to only run one application at a time and to open it using a terminal.

That way, you can see what is going on and you will be able to see what actually happens when your system / application freezes.

A few  questions.

1. Is it hard locks that you are getting? ie keyboard, mouse are inoperative?

2. Can you escape the lock by CNTL>ALT>BACKSPACE?

3. Can you kill the errant application?

Regards,
Roger :cool:

---

### Post by sfeone on 2008-04-19
Hi, Roger!!

Thank you for your interest on my asking.

When I am in this serious problem, I can not control my computer: mouse, keyboard and so on.
Even I cannot escape from the screen saver.

As a result, I cannot help pressing the power button.

Can you give some solution for me?

Han....

---

### Post by ramjet_1953 on 2008-04-19
OK, as I said before, run your application by first opening them in a terminal.
That way you can monitor what is going on.

i.e. Open a terminal and if the application's name is "fred", just type in [COLOR="Red"]fred[/COLOR], followed by a CR.

Also, how much RAM do you have?

When a system freezes, the [COLOR="Blue"]ABSOLUTE LAST[/COLOR] thing that you do is power down.
If you get a hard lock do this in the order listed, to safely shut down.

NOTE: Be sure to wait a few seconds between each step.

1. Alt+SysReq+r

2. Alt+SysReq+s

3. Alt+SysReq+e

4. Alt+SysReq+i

5. Alt+SysReq+u

6. Alt+SysReq+b

To remember this sequence, memorize this:

[COLOR="Red"]R[/COLOR]aising [COLOR="Red"]S[/COLOR]kinny [COLOR="Red"]E[/COLOR]lephants [COLOR="Red"]I[/COLOR]s [COLOR="Red"]U[/COLOR]tterly [COLOR="Red"]B[/COLOR]oring

Regards,
Roger 8)

---

