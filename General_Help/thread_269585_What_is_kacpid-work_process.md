---
title: "What is kacpid-work process?"
date: 2006-10-01
forum: General Help
---

### Post by kernco on 2006-10-01
I've been having trouble with Ubuntu getting so slow that it is basically frozen.  I ran 'top' and waited for it to happen, and I noticed that at the time it is frozen, CPU usage is at 100% and there are a bunch of processes called kacpid-work-1, kacpid-work-2, etc.  I guess it is forking in an inifinite loop?  What is this process and why would it do this?

---

### Post by keithpeter on 2007-01-03
I would like to know what kacpid-work-x is about as well. I'm not getting huge slowdowns, but I have a kacpid-work-2 process running now that is claiming exactly the same amount of RSS as OpenOffice. When I first noticed this, the process was loaded with exactly the same RSS as Firefox, the largest program I was running at the time.

I've booted using the linux-686 kernel on a P3 700MHz laptop running Xubuntu 6.06, and I loaded up a lot of software. For the first hour or so, kacpid-work-0 and 1 ran in 224K of RSS low down in the task manager. Then this work-2 process started. The screen grab included shows the XFCE4 task manager, free and top.

Is this a 'real' process? I have not been able to reproduce the behaviour in the linux-386 kernel as yet but I shall try again. 

Any pointers to information?

---

