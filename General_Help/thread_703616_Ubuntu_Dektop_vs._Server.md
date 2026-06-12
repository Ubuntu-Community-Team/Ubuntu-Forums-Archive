---
title: "Ubuntu Dektop vs. Server"
date: 2008-02-21
forum: General Help
---

### Post by ftwda on 2008-02-21
Hi all, 

My department is looking for buying new workstations. These will be workstations with double Intel Xeon Quad Core CPUs (i.e. they will be strong ones:) They will mostly be used for mathematical computations (i.e. optimization algorithms mostly). There will be a few users (3 or 4 in worst case) to connect these computers via SSH to run their own codes (or some optimization software). There will be no other servers installed on these workstations.

I want to know if in terms of calculation performance would Ubuntu Server and Ubuntu Desktop (64 bit versions of both) make difference? And if yes, how much?

Thanks, 
Baris

---

### Post by blazercist on 2008-02-21
its really the same identical kernel so they will be the same.... the only difference will be the packages installed and hence overhead, desktop adds a bunch of stuff that is graphical and user freindly which uses up some resources and server is all command-line with a bunch of you guessed it - server software - in general if you dont need a pretty graphical user interface then I would use the server version because I THINK* it uses less system resources for overhead.

---

### Post by bodhi.zazen on 2008-02-21
Actually the server comes with the server kernel.

[http://packages.ubuntu.com/gutsy/linux-server](http://packages.ubuntu.com/gutsy/linux-server)

It is designed / optimized for networking.

To be honest, I doubt you will see much difference between the server and desktop versions. Depending on how familiar you are with the command line :

1. Not at all -> Go desktop & learn the CLI

2. Familiar enough not to "need" a gui -> Go for the serer edition.

3. Expert. Go for a minimal install and add only the services / applications you need on the server. This will be fastest.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

============

I also advise you go 64 bit. 64 bit should give you a 10-30 % boost in computing power.

---

### Post by jespdj on 2008-02-21
> **bodhi.zazen said:**
> I also advise you go 64 bit. 64 bit should give you a 10-30 % boost in computing power.
If your primary goal for these servers is mathematical computations, then definitely go for the 64-bit version for more computational performance.

Note that the 64-bit version is labelled "AMD64", don't be confused by the naming, it does not mean that it runs only on AMD processors - it's meant for AMD as well as Intel processors that support the 64-bit x86 instructions (which includes the Intel Xeon quad core CPUs you're looking at).

---

### Post by ftwda on 2008-02-22
Thank you all for help,

First of all I am pretty sure about the 64 bit version :) I use 64 bit in my laptop, too.

I am mostly OK with using Command Line but of course for personal usage. I am not sure if I can handle everything w/o the gui.

Let me ask you another thing. What if I install the desktop version but use the GUI whenever I require and stop GDM afterwards ?

---

### Post by bodhi.zazen on 2008-02-22
That works, I always disable GDM and boot to the command line.

You can start your gui with startx, gnome-session, startfluxbox, startkde,xfce4-session ....

---

