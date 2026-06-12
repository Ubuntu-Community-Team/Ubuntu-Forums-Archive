---
title: "Nvidia driver for Feisty"
date: 2007-04-11
forum: General Help
---

### Post by tegwilym on 2007-04-11
Ok, I'm at my wits end trying to get this working again.  I've had wonderful luck using the new 7.04 Feisty and it's fantastic! 
My problem is that now and then when I'm experimenting I'll mess it up so badly that I have to reinstall the OS.  No big deal, it sure goes on easier and faster that M$ crud!  :) 

So this should be a simple question. I'm running an Nvidia card (I forget exactly, I think it's the 6200) which works just fine.  But....when I reinstall it's trial and error to find what driver allows me to use multi monitor.

What is the name of the file that I have to install that will give me the enhanced Nvidia configuration options?  I just keep ending up with that simple "information" thing in the Applications -> System tools -> Nvidia settings.

When I get the one called "Nvidia server settings" (or whatever it is called) I get the features I want, but I just can't find the darn thing.  
Help!!

Tom
Working hard at escaping the grip of Microsoft.

---

### Post by MoLE on 2007-04-20
> **tegwilym said:**
>  But....when I reinstall it's trial and error to find what driver allows me to use multi monitor.

What is the name of the file that I have to install that will give me the enhanced Nvidia configuration options?  I just keep ending up with that simple "information" thing in the Applications -> System tools -> Nvidia settings.


nvidia-settings is the correct program, however you need a recent driver and a card that is supported by that driver.

I have a GeForce4 Ti 4800 SE - quite an old card now, and I can access the Twinview settings using this tool.  I am using the 9631 drivers in the feisty repository - the package is nvidia-glx.  If you are using nvidia-glx-legacy, then the twinview settings will not be available.

You can check by going in to System -> Administration --> Synaptic  and doing a search for "nvidia-glx".  You should then be able to tell whether you have the correct package installed.

If you are using the restricted driver manager, it should detect the correct package for you when you enable restricted drivers.

---

### Post by tegwilym on 2007-04-20
Thanks.  I did get it working again on 2 monitors and just installed 7.04 yesterday.  
Beryl works easily on my computer at home, but my work computer I get the infamous "black screen" thing.  The effects to seem to work, but I can't see anything other than edges moving around, and they flicker badly too.  
Work computer is nearly identical to my computer at home, but it just gives me problems getting it working.  I did get Beryl working once on one monitor on my work computer, but messed around with something, killed it, and now I don't know what I did to get it working!
....so that is my latest issue.

Tom

---

### Post by MoLE on 2007-04-20
Tom,

You might want to update your forum profile - I'm sure you're not still running breezy!

I'm far from a Beryl expert, but I've played with it enough to know that it breaks. A lot.  I know it's difficult, but you might just be better off putting it aside for a while.  Personally I wil be using it a lot more once the compiz/beryl code merger has put out it's first release.

Have fun!

---

