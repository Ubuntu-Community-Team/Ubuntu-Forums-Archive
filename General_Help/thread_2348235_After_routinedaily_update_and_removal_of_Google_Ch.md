---
title: "After routine/daily update and removal of Google Chrome, now stuck in login loop"
date: 2017-01-01
forum: General Help
---

### Post by stevecro2 on 2017-01-01
Ran some small routine/daily updates from my 14.04.5 LTS, also did removal (using Synaptic Package Manager) of my old Google Chrome (it was saying that it wasn't supported any more on my version of Ubuntu, anyway). No major or distribution upgrades (yet) (although I would like to do that after I get this fixed).

But now after I login, I get the pink screen, but it never gets to desktop, and after a while, does drum roll sound and bounces me back to login. Also get pop up window "System Program Problem Detected" to which I answer "Report..." (does anyone ever read those?)

Tried doing "mv .Xauthority .Xauthority.bak" that I found with a Google search, from a console prompt (login there still works), but that didn't help.

Found a file called xsession.errors being generated -- that I think was in my home folder -- but when I try to find it over there in my home folder now (doing this from another partition with another distribution that allows me to bring up graphical for browser, etc.), it appears to have been deleted when I rebooted to get into the (non-Ubuntu) partition that I'm in now.

Is there a repair that I can run, or something that I can download, to get the graphical login working in my Ubuntu partition again?

---

### Post by stevecro2 on 2017-01-02
OK, my .xsession-errors file (now I've got the name right ;)) was a hidden file and now I've found it. Here is what it looks like:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: update-notifier-crash (/var/crash/_usr_bin_compiz.127.crash) main process (2509) terminated with status 1
init: update-notifier-crash (/var/crash/_usr_sbin_unity-greeter.122.crash) main process (2511) terminated with status 1
init: gnome-session (Unity) main process (2553) terminated with status 1
init: Disconnected from notified D-Bus bus
```

and I also had a .xsession-errors.old, which looked like this:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped
init: gnome-session (Unity) main process (3576) terminated with status 1
init: Disconnected from notified D-Bus bus
```

I hope this helps, thanks in advance for any help!

---

### Post by stevecro2 on 2017-01-02
Also, I had given up on the default (I think it's called Unity) desktop a while back when I had less RAM, and just went back to Gnome; now even though I have 4G, I was still sticking with Gnome. Thanks again.

---

### Post by mörgæs on 2017-01-02
If you have 64 bit hardware you could consider a fresh install of a 64 bit 16.04.1, erasing the 32 bit 14.04. 
It gives better use of your 4 GB memory and it has access to Chrome.

---

### Post by stevecro2 on 2017-01-02
Thanks for your goodwill and helpfulness, but I'd rather not "sink the ship to save it" just yet, until it becomes a last, or almost last, resort. :P 

I tried adding a new user with admin privileges, and also trying to fire up different desktops from the login menu (was using Gnome Metacity, tried just Gnome and also Compiz), same thing (or maybe not even that much -- just sitting on gray screen and I rebooted from the console prompt -- no problem logging in there).

I am wondering, though, about that ugly "System Program Problem Detected" box that *always* comes up right after my login, and where I click "Report...". Is there any way to get it to tell me *what* the "problem" is? Something tells me that that would be helpful. Again, thanks for any help!

---

### Post by #&amp;thj^% on 2017-01-02
> **stevecro2 said:**
> 
I am wondering, though, about that ugly "System Program Problem Detected" box that *always* comes up right after my login, and where I click "Report...". _**Is there any way to get it to tell me *what* the "problem" is? Something tells me that that would be helpful. Again, thanks for any help!**_

If you want to see the details look in **"/var/crash/ "  **for any new reports.

---

### Post by mörgæs on 2017-01-02
> **stevecro2 said:**
> 
I am wondering, though, about that ugly "System Program Problem Detected" box that *always* comes up right after my login, and where I click "Report...". Is there any way to get it to tell me *what* the "problem" is? Something tells me that that would be helpful. Again, thanks for any help!

It might be helpful to see the message but don't report bugs in 14.04. They are unlikely to be fixed.

If the bug report concerns 17.04 (development version) it will get more attention. Maybe off topic, but just to prevent wasted effort.

---

### Post by stevecro2 on 2017-01-03
OK, this is weird, but now I really learned something tonight. I got a desktop to come up! 

How? 

When the first login prompt came up, I did the drop-down and instead of choosing one of the desktop options that I had been trying to get to work (has always been a Gnome variation, like Metacity (that I had been using before everything fell apart), or Compiz, or just Gnome, or maybe I took "Ubuntu Default") -- this time I tried something different: "KDE Plasma Workspace" (I already use KDE on another distro that I have (SuSE).

KDE came up fine, and that is where I am writing this from. I did get a "System Program Problem Detected" box pop up, but this one allowed me to see some detail, and said that something like "packagekitd" had failed. (I think this might have very little to do with the box that was popping up right after login with the Gnomes.)

I would like to go back to Gnome with this Ubuntu, but I'm not sure what I've proven. Ideas? Thanks again for thoughts... ;)

---

