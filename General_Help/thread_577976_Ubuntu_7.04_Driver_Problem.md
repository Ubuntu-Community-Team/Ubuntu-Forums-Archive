---
title: "Ubuntu 7.04 Driver Problem"
date: 2007-10-16
forum: General Help
---

### Post by vonfeldt7 on 2007-10-16
I ordered an 8600GTS and just installed Ubuntu 7.04 (Dual Booting with Vista) and I want to use the drivers Nvidia offers ([found here]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html")).

I thought this would be a simple enough task, but I forgot that in Linux (or at least ubuntu) NOTHING is simple, and everything is overly complicated. So I try to take the dumbass [linux] way of doing things. I downloaded the file to my desktop, its a .run file. I got it to successfully run in the terminal, since its text based, but then I get this

> 
ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com)

So basically...I guess I need to close X Server? (Or do I not need to?) How do I do this? It says to download some thing from them that edits the Config file for you, but I can't get it to work either.

Can ANYONE just please help me to install these drivers? I never dreamed it would be this difficult..(but I'm used to Windows OS......you know...the OS that actually works and gets things accomplished without a P.H.D. in computer technology?

---

### Post by r-mo on 2007-10-16
Goto System->Administration->Restricted Drivers Manager

There should be a tick box for the proprietary nvidia driver.

If that isn't the case, or you really want the most recent driver you could try envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

BE WARNED though installing either from the .run or with envy may well break your system when you update to gutsy (which has the most recent driver, btw, and only 1 day away)

---

### Post by vonfeldt7 on 2007-10-16
> **r-mo said:**
> Goto System->Administration->Restricted Drivers Manager

There should be a tick box for the proprietary nvidia driver.

If that isn't the case, or you really want the most recent driver you could try envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

BE WARNED though installing either from the .run or with envy may well break your system when you update to gutsy (which has the most recent driver, btw, and only 1 day away)

I've already tried the restricted drivers and it says I don't need them, I'll try "envy" and tell you it goes...I'm sure it won't go to plan though because nothing i ever do in ubuntu actually works like its supposed to.

and im not worred if it "breaks my system" i've reinstalled ubuntu over 15 times in the few weeks i've tried it, im used to reinstalling by now

---

### Post by vonfeldt7 on 2007-10-16
> **vonfeldt7 said:**
> I've already tried the restricted drivers and it says I don't need them, I'll try "envy" and tell you it goes...I'm sure it won't go to plan though because nothing i ever do in ubuntu actually works like its supposed to.

and im not worred if it "breaks my system" i've reinstalled ubuntu over 15 times in the few weeks i've tried it, im used to reinstalling by now

*edit*

THANK YOU!!!!

Envy worked, and it even installed correctly!!!!!!! (which in my experience, hardly ever happens in ubuntu)

---

### Post by vonfeldt7 on 2007-10-16
> **vonfeldt7 said:**
> *edit*

THANK YOU!!!!

Envy worked, and it even installed correctly!!!!!!! (which in my experience, hardly ever happens in ubuntu)

*EDIT 2*

Well I tried to install Beryl...and....BOOM goes the OS....

I guess I get to reinstall it once again, doesn't surprise me 

Why most this OS be so crappy?

---

### Post by jocko on 2007-10-16
> **vonfeldt7 said:**
> *EDIT 2*

Well I tried to install Beryl...and....BOOM goes the OS....

I guess I get to reinstall it once again, doesn't surprise me 

Why most this OS be so crappy?

You really can't break the whole os by installing beryl, but you may mess up your x server if you really don't know what you're doing.
That should be easy to fix, just change everything back to how it was before you messed things up.
You really don't have to reinstall the whole os.
If you don't know how to fix it, just explain what you did to break it, and I'm sure someone will have a solution to fix it.

If the os is so crappy, why do you bother trying to use it?
If you're happy with windows, why don't you stay with it?

---

### Post by Sef on 2007-10-17
> Well I tried to install Beryl...and....BOOM goes the OS....

Beryl is not being worked on now.  Instead Compiz-Fusion is being worked on.   It is in an alpha state, i.e., it is unstable and will not always work.

---

