---
title: "Gusty very slow on my laptop"
date: 2007-11-17
forum: General Help
---

### Post by RudolfMDLT on 2007-11-17
Hi there,

I have a HP nc6000 laptop that is running very slowly in Gusty. It has 512mb Ram and a 1.6Ghz Pentium M processor. Now I have done some of my own tweaking, and removed some unnecessary things from boot up and start up that came pre-installed with Ubuntu Ultimate Edition.

Is there anything that anybody can suggest I do to speed things up a little? Any tweaks that might get this laptop ticking again? :)

Is it possible to upgrade a laptop's cpu?

Thanks for any general advice and tips!

Rudolf

---

### Post by HermanAB on 2007-11-17
Hmm, that processor is plenty fast enough.  Run 'top' to see what is chewing the processor.  Don't run Beryl.  Don't run desktop search.  Don't run Gnome or KDE. Install Xfce (Xubuntu)  or IceWM instead and it will zoom like a new machine.

Cheers,

Herman

---

### Post by cotcot on 2007-11-17
Dou you see any difference when the laptop is on battery or on the power net ?
HP laptops reduce cpu speed when they are on battery to lengthen battery time. I have seen a 1.6 GHz been turned down to 0.8 GHz (even lower) because of this. 

If you use compiz or vmware or so some additional ram would help as well.

---

### Post by RudolfMDLT on 2007-11-17
I forgot about the desktop search! Thanks, I'll install XUbuntu and IceWM and see what works best!

Thanks!

Anything else anybody!? :)

---

### Post by Sallyje on 2007-11-17
I am new to linux and ubuntu.  I have installed ubuntu on my sons slave ide drive 80gb.  The computer is a amd machine with 512 ram primary a window xp sp1.  It is running very very slow.

[LIST]
[*]If I install xubuntu xcfe would I have to start all over again.
[*]Could it be firefox?
[*]does the ubuntu installation affect windows which is also running slow on the machine
[/LIST]

I would like to be converted 

Sallyje

---

### Post by cotcot on 2007-11-17
I also saw a HP laptop having 256 ram only showing 192 because 64 was used by the graphics.

---

### Post by RudolfMDLT on 2007-11-17
> **Sallyje said:**
> I am new to linux and ubuntu.  I have installed ubuntu on my sons slave ide drive 80gb.  The computer is a amd machine with 512 ram primary a window xp sp1.  It is running very very slow.

[LIST]
[*]If I install xubuntu xcfe would I have to start all over again.
[*]Could it be firefox?
[*]does the ubuntu installation affect windows which is also running slow on the machine
[/LIST]

I would like to be converted 

Sallyje

No, in synaptic you can just add XCFE. when you login, there will be an option for session. select XCFE and it will load instead of Gnome.

---

### Post by RudolfMDLT on 2007-11-18
Thanks! I haven't installed XFCE yet, but removing all the other junk took my initial memory usage down from 364mb to 126mb! And it's fast enough again! Thanks!

---

