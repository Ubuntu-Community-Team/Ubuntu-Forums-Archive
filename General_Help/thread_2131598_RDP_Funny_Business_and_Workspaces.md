---
title: "RDP Funny Business and Workspaces"
date: 2013-04-02
forum: General Help
---

### Post by MacAodh on 2013-04-02
Hi there,
I'm having a bit of a funny one with remina remote desktop. I couldn't get it working until I removed it from the known hosts file. Now it's connecting perfectly. However I have a new problem. I use a second monitor in work attached to my laptop, I want remote desktop on my external monitor and remainder on my laptop. When I open it it automatically goes to the second workspace (One on the right) and when I try to drag it over it won't stay there. I could get over this however it then jumps, almost every time I use it and then go out of it (to a program on my computer) it will jump screens. Always in either the first or second work space but randomly between the four possible screens in those work spaces (Monitor/laptop screen in both work spaces). Then when I click on it some times it will work and sometimes it will jump in which case I have to find it again before I can use it.

Can I A: Stop it jumping and B: disable the extra workspaces, I never use them and they just annoy me honestly. I tried using this:

gconftool-2 --type=int --set /apps/metacity/general/num_workspaces 1

However this doesn't seem to have stopped it, still got multiple workspaces...

This is really a bit bothersome if someone was able to cast some light on this it would be great.

Cheers 

Conor

---

### Post by MacAodh on 2013-04-03
Hi Guys,
A quick update. I've installed Compiz settings manager and reduced the amount of workspaces to one. Effectively removing the workspaces. But I'm still having the issue with remina jumping from one screen to the other. It now seems to be formatted to my laptop display however the top bar only appears when It's in the external monitor. Also, it doesn't appear to occur unless it's in full screen...

Is there any way to set a program to default to one screen rather than another? Even setting up a default main screen or something... I also see odd behaviour such as everything moving to my external monitor (programs) when I connect it. Bloody infuriating as, for example, if I'm adding an attachment to an email the folder comes up on my second monitor rather than the one i'm working on.

---

### Post by MacAodh on 2013-04-03
Riiiiight,
I've made a couple of changes, none of which seemed to work. Many people are suggesting changing settings on compiz manager however all changes don't seem to be making a difference.

Currently I've two issues: how does one set one desktop as priority and two; how can one stop remina from jumping from screen to screen???

Any help on this would be great guys

---

