---
title: "Dell XPS 15 on Lubuntu, still slow! :/"
date: 2014-09-10
forum: General Help
---

### Post by guit4eva on 2014-09-10
Hey guys,

I have a Dell XPS 15 which should be pretty fast, especially on Linux, but no matter which distro I try (Mint Cinnamon, Mint XFCE, Antergos, OpenSUSE, Fedora, ubuntu, Lubuntu etc etc) it still gets slow after open for a while and then eventually freezes and I have to hard reset. At the moment, I'm running the latest Lubuntu, nearly all my ram is being used, even swap is being used, and all I have open is:

1) Chrome
2) Netbeans
3) Gimp

At the moment, the highest RAM usage in htop is NetBeans with 8.7%, and the highest CPU usage is 18% with Chrome, so I  don't know where all my RAM is going.
The CPU monitors seem fine, but RAM usage is between 4 and 5gb of my 6gb, and 2gb to 3gb of the 6gb swap is being used.

Does anyone have any ideas as to why it would keep getting slow all the time? I'm out of ideas as to what to check for. Is my laptop possibly just not a good choice for running linux?

---

### Post by walterorlin on 2014-09-10
The thing is are you loading lots of files to and from a harddrive as that could be a problem if you are I/O bound does that have a solid state drive or a spinning hard drive. Also chrome can open mulitple tabs which is not just one window with tabs if you have 100 tabs open that is not the equivlent of having just chrome open. Also are you running the code locally in netbeans. Gimp does load grahpics and chrome could have video ads which could make you bound by video as well. Also did you have lots of stuff open before or are those the only programs you ran since you booted? sometimes libraries load to memory and then don't get unloaded unless you logout or reboot. Another solution short of fast reseting may be watching in htop and when it starts to get slow logout and start a new session but a little annoying. As this will lower ram use. 

Also with GIMP you should note how many pictures you have open and tabs in chrome. Also have you installed lots of other stuff it could be libraries that load or small things that autostart but that shouldn't matter that much with 6 gigs or ram.

---

### Post by oldfred on 2014-09-10
It is normal for RAM to look like it is used.
 Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

But with 6GB of RAM you should never be using swap, and that will be very slow. My 4GB desktop never uses swap, but then my normal use is to only load a few apps at once as my laptop has only 1.5GB of RAM and uses swap and is then very slow if I try to load more than one large and a couple of smaller apps.

---

### Post by guit4eva on 2014-09-12
Hey guys,

I had my swappiness set to 60, so that might have been a potential cause. I've changed it to 10 now and will see how that works out. Thanks for the help and links, I'll report back if changing the swappiness doesn't work, but it seems to be better so far :)

---

### Post by vasa1 on 2014-09-12
> **guit4eva said:**
> Hey guys,

**I had my swappiness set to 60**, so that might have been a potential cause. I've changed it to 10 now and will see how that works out. Thanks for the help and links, I'll report back if changing the swappiness doesn't work, but it seems to be better so far :)60 is the default on Lubuntu 14.04.

---

