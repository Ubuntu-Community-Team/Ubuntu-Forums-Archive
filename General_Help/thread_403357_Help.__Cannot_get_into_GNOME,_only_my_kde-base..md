---
title: "Help.  Cannot get into GNOME, only my kde-base."
date: 2007-04-06
forum: General Help
---

### Post by darweth on 2007-04-06
Check this!  I understand if you do not wish to assist me because I was acting in a treacherous manner to the Ubuntu community and attempting to install Arch Linux.

So I have a slave drive... it consisted of ONE partition solely devoted to my music collection.  I backed this piece up on an external and set it as my master drive (my previous Ubuntu disk removed to a safe location offshore).  I installed Arch on it and formatted it.... that is another story.

Anyway, I safely retrieved my Ubuntu master and popped it in.  Everything boots up as normal, but I cannot log into GNOME.  EEK.  Gnome comes up and my panels and that box with the startup crap before the screen goes PITCH black!  The Nvidia logo and gdm greet me after a few seconds of waiting.  I can log into my minimalist kde-base FINE, however.  I never use kde though, so who cares? ;)

I will tell you the only change I made.  Obviously my previous slave drive is now the Arch disk.  Still, I maintained my fstab anyway for the hell of it.  Is that what is causing the problem?  Can an invalid entry in fstab really prevent GNOME from loading?  WOW!  Why does kde load then?  I will of course test this hypothesis shortly, but wanted this up here just in case and as a warning to future people in my condition.  

Thank you for reading and any hints/help/assistance you might offer.

***EDIT***

Ah.  In very unfortunate, but not unexpected, news.  I did strike the non-existant drive from the fstab and it had no effect.  Gnome blacks out and boots me back into gdm.  Damn!  I have never had a problem with it.  What is going on???

---

### Post by darweth on 2007-04-06
A little more information I should have added.

I had a USB external drive going and forgot to exit before I attempted that Arch install.  I wonder if that is a partial source of the problem (I shut it down after).  Turning it back on does not resolve it for the moment there.

Here is the update:

Tried FAILSAFE GNOME and get some info tidbits that pop up way too fast and vanish once again to the black screen and gdm.  Here is what I am able to gather.

"Unable to determine the address of the message bus."  I am assuming this is a dbus issue.

"I've detected a panel already running... quitting"  (i think a quit msg is there at least.  It goes way too fast and I cannot remember).

---------

I tried a killall gnome-panel in the terminal within KDE and it did not change anything.  



Any tips on what to do to correct this?

---

### Post by zvacet on 2007-04-07
```
sudo /etc/init.d/gdm start
```

And you can look this page

[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by darweth on 2007-04-07
Well, I would just like to say I never did get this problem solved and just gave up since I was installing Arch anyway.

I will encourage people to research this issue for the future though.  If you do a search on "Unable to determine the address of the message bus" here on the forums, you will find numerous people with this issue.  Some really kooky fixes have worked for some, but others have just given up and cried.  

Have no fear!  I am enjoying Arch for now, but I will definitely be back to Ubuntu in the future.  It was my first Linux love and will continue to be the sole distro that I HEAVILY recommend for the average Joe.

---

