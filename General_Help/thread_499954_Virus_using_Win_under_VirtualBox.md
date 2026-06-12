---
title: "Virus using Win under VirtualBox?"
date: 2007-07-13
forum: General Help
---

### Post by gaiterin on 2007-07-13
Hi!
I use Windows XP (without antivirus) by VirtualBox some times, under Ubuntu.
Can a win virus infect the Ubuntu system when I use Windows by VirtualBox?
It's surely for Ubuntu use Windows?
Thanks.
Marcos.

---

### Post by zero244 on 2007-07-13
Highly unlikely............it can only effect your Windows installation...........Linux is immune to Windows Viruses.

---

### Post by InKo on 2007-07-13
I doubt it can.

well,
1. the most viruses for windows are written in assembler - so NO
2. to infect the linux you  must have root privelegs; if you run as user - NO again
3. virus has to re-compile itself on linux plattform to be executable - I NEVER heard about that.

more ideas? :)

---

### Post by smoker on 2007-07-13
no, plus if you make a 'snapshot' of a clean virtualbox install of xp, then when you use the snapshot, the infected version will be gone!

---

### Post by gaiterin on 2007-07-16
Hi.
Thanks very much by all answers! :)
I find a interesting web (in spanish), about this:
[http://www.nosololinux.com/2007/04/16/consultorio-nsl-virtualizacion-y-antivirus/](http://www.nosololinux.com/2007/04/16/consultorio-nsl-virtualizacion-y-antivirus/)
Bye!
Marcos.

---

### Post by shane2peru on 2008-01-18
Sorry to dig up an old thread, but I thought coupled with this question should be, What about a firewall?  I too am running Windows under virtual box, and running it without Firewall and Antivirus kind of feels like running around naked.  Can it be hacked?  Thanks.

Shane

---

### Post by Sam on 2008-01-18
> **shane2peru said:**
> Sorry to dig up an old thread, but I thought coupled with this question should be, What about a firewall?  I too am running Windows under virtual box, and running it without Firewall and Antivirus kind of feels like running around naked.  Can it be hacked?  Thanks.

Shane

No, because:

1) You're probably connecting to the net from your Windows through VirtualBox' NAT. This way nobody can connect directly to your Windows from the net.

2) Even if you download and run something bad, if you previously made a snapshot of your clean system, just revert back and it'll be gone.

---

### Post by shane2peru on 2008-01-18
> **Sam said:**
> No, because:

1) You're probably connecting to the net from your Windows through VirtualBox' NAT. This way nobody can connect directly to your Windows from the net.

2) Even if you download and run something bad, if you previously made a snapshot of your clean system, just revert back and it'll be gone.

Thanks Sam, that leads me to my next question, is NAT the best way to have your virtual OS connected?  I kind of figured that was the case as far as protection from Linux, it is just really odd to be running Windows without any protection. :)

Shane

---

### Post by gvartser on 2008-01-18
There is a quick fix for this, which protects your windows installation.

1) Do not allow it to connect to the Internet.

or "If you need your connection"

2) Download and install Apani Antivirus. 
It is free for home usage, you need to register and you get 12 month for free, when the time is up you need to re register again to get another free 12 month.
I use Apani on my Vista guest OS, and it works like a charm.

Best regz,
/G

---

### Post by Sam on 2008-01-18
> **shane2peru said:**
> Thanks Sam, that leads me to my next question, is NAT the best way to have your virtual OS connected?  I kind of figured that was the case as far as protection from Linux, it is just really odd to be running Windows without any protection. :)

Shane

If you need a simple internet connection for your guest, yes NAT is the best.

There is also Host Interface if you need to create a full network with multiple guests, however this is tricky to get it working, you need to create a bridge on the host, etc... Search if you need more info about this..

---

### Post by shane2peru on 2008-01-18
> **gvartser said:**
> There is a quick fix for this, which protects your windows installation.

1) Do not allow it to connect to the Internet.

or "If you need your connection"

2) Download and install Apani Antivirus. 
It is free for home usage, you need to register and you get 12 month for free, when the time is up you need to re register again to get another free 12 month.
I use Apani on my Vista guest OS, and it works like a charm.

Best regz,
/G
  That did cross my mind being the paranoid person I am.  :)  However, I'm having trouble getting files to my Virtual OS, and out of there, thinking about uploading them to my web site as a temp fix, kind of annoying, but I don't know another way right now.  I re-installed VirtualBox with the one from the website, however I still don't seem to have this USB option.  Not sure what to do to fix that, but I guess that is for another thread and another day.  Thanks for the info.  

Shane

---

### Post by gvartser on 2008-01-22
> **shane2peru said:**
> .  I re-installed VirtualBox with the one from the website, however I still don't seem to have this USB option.  Not sure what to do to fix that, but I guess that is for another thread and another day.  Thanks for the info.  

Shane

To get the USB to function you need to install the non-free version:

Check out this link: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

And if you are using GUTSY 7.10 you also need to do this:

Link: [http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

Good luck,

/g

---

### Post by shane2peru on 2008-01-24
Thanks!  I did those things and got it working.

Shane

---

