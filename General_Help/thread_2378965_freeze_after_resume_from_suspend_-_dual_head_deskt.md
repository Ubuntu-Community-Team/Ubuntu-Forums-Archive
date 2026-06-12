---
title: "freeze after resume from suspend - dual head desktop"
date: 2017-11-29
forum: General Help
---

### Post by drechsel on 2017-11-29
My system:
ubuntu 17.04
gnome desktop
4GB RAM
2x3GHz core duo
NVidia GT 630
two monitors
driver set nvidia 384 

Hello,
by now my system will freeze nearly daily after resume from suspend to RAM. In a terminal, at "top" Xorg reads close to 100% CPU load, irq/28-nvidia round 13%. Most times the mouse pointer still can be moved, but no other input is accepted.

Here are the most recent Xorg.log files:
[https://owncloud.trolink.de/index.php/s/lB0qWWQ0LLk5mRz](https://owncloud.trolink.de/index.php/s/lB0qWWQ0LLk5mRz)

My system has been suffering from this problem for years, sometimes more, sometimes less serious. It occurs with one monitor as well as with two, and with different video cards. Even the standard resume procedure is weird - I filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384/+bug/1733168](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-384/+bug/1733168)
.
What can I do to track down the problem?

Cheers,
Wolf

---

### Post by drechsel on 2017-12-12
To answer my own question:
The nvidia package 384 seems to be a nasty beast on my machine. Reverting to 340 brought me back a rock solid system.

So: Fellows who are experiencing video problems might want to go back to a prior driver version. It is very easy by using the software-properties application, tab "additional drivers" (or is it "proprietary drivers" ?)

---

### Post by teafx on 2017-12-12
I was having suspend/resume issues as well with Ubuntu and Nvidia. Switching drivers may only be one remedy and not necessarily a complete one. I actually had a difficult time getting it to never happen as it would randomly happen too.

Its so ridiculous that for me at least even waiting 48 hours might resolve the issue for some time. It was so crazy that I remember having corrupted screen on resume too.

Finally, I used it as an excuse to move to the latest version of Fedora (Fedora 25 at the time) and no longer had a problem after using negativo17 provided driver (though am using Nvidia's own driver right now with Fedora 27).

So if you find it continues to happen, might I suggest Fedora. It has its own problems and by the time you finish setting it up with your applications, etc Fedora is understood, but its so nearly the same as Ubuntu. I don't understand why people say one is better than the other or have an attitude towards certain disto's. They're both really very similar.

With all the suspend/resume Nvidia issues (I've seen 4-5 completely different issues) on Ubuntu I just couldn't take it anymore =)

They seriously need to work on that getting it to work properly with hardware. Never was suspend/resume so bad. I literally thought my GPU must be going bad or getting too old for the latest drivers but its the same GPU today and working great on Fedora with the latest drivers. Seriously, they need to actually fix this.

---

