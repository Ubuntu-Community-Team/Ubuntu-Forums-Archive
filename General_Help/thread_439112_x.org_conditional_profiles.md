---
title: "x.org conditional profiles?"
date: 2007-05-10
forum: General Help
---

### Post by mattmcmanus on 2007-05-10
I was just thinking about this, I doubt it is possible but I figured i'd post it anyway. 

I've got a laptop. When I have it at home, I hook it up to a external monitor and, obviously, when I am not home I just use the laptop screen. Everytime I restart when I am at home, if I leave the mointor plugged in X notices it and uses it, but at the wrong resolution (640x480 i think..which fouls up the placement of my system tray and clock and all of that.)

My question is this: Is there anything out that the can do conditional profiles for x? So if I boot it up and  it notices the external monitor it will use a xorg.conf file that is properly set up and if it that fails then to default to a standard, safe xorg.conf file? 

I know I could just do this with good ol' cp but I dont want to have to copy back and forth all of the time. 

Thoughts?

---

### Post by kidders on 2007-05-11
Hi there,

I'm sure you could have Linux do the copying automagically ... it would be a matter of finding something that's different about your laptop, when it's at home. (Availability of a particular wireless network, maybe?)

Any ideas?

---

### Post by mattmcmanus on 2007-05-11
I've actually been thinking about that alot lately. There are a number of things that I would like to be different depending on where I am at at the time. Wireless network is a great way to do that. 

I wouldnt know the first place to start thought. I've been using Ubuntu for a couple months now but im not that comfortable. 

Anyone else have any ideas of a peice of software that takes care of this?

---

### Post by kidders on 2007-05-12
> **mattmcmanus said:**
> I wouldnt know the first place to start thought. I've been using Ubuntu for a couple months now but im not that comfortable.You should give it a try ... you might surprise yourself! :-P

_My_ approach would be to write a new service (ie something that would "start up" during boot (ie rewrite a few configuration files), and "stop" when you shut down (ie return them to a default, failsafe state).

Imagine, for the sake of argument, you wanted to do something like...
[LIST]
[*]Enable loosened Samba file sharing access restrictions when at home, but throw up a brick wall when you're in a more public place.
[*]Preconfigure Xorg so it works 100% properly with multiple displays, when at your desk.
[*]Increase battery life by clocking down your CPU ... but only when you're not at home.
[/LIST]

You might do three things:
[LIST]
[*]Create a script (perhaps called /usr/local/bin/whereami) that spits out a name for your current location (eg "home" or "away"), based on some sort of criteria ... like the list of available wireless networks.
[*]Set up a small repository of configuration files (perhaps somewhere like /opt/sysconfig) optimised for each location ... such as xorg.conf.home, or smb.conf.away.
[*]Have your custom service preconfigure applications using these files, based on the output of "whereami".
[/LIST]

Quick example...
[LIST=1]
[*]Force Samba to stop. (**/etc/init.d/samba stop**)
[*]Reconfigure it. (**cp /opt/sysconfig/samba.`whereami`/etc/samba/smb.conf**)
[*]Start Samba back up again. (**/etc/init.d/samba start**)
[/LIST]
Like you mentioned, another poster may be aware of something that can already do this sort of thing.

---

