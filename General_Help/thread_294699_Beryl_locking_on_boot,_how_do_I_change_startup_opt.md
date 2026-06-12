---
title: "Beryl locking on boot, how do I change startup options for gnome from terminal"
date: 2006-11-07
forum: General Help
---

### Post by Jason.TJ.Johnson on 2006-11-07
Anyway, here's the deal.

I'm a fairly new Ubuntu (and Linux) user and for the record I'm loving it! I've sucessfully installed Edgy Eft (as well as 6.06 in the past) as well as Automatix, a crap-load of other software and I'm able to configure it pretty well.

Anyway, here's the deal. I tried to install Beryl and XGL and everything was working correctly during the installation process until I ran beryl manager. When I run it, the title bars to all windows disappear and both the top menu bar and the bottom bar disappear as well. ALT+F2 doesn't work and it appears (though I'm not sure) that X locks up.

So, I CTRL+SHIFT+BCKSPCE and X restarts normally. I try to login, the tittle bar disappears and it appears to lockup again.

So, I reboot completely. Log back in and same deal.

So I tried logging in via the Fail-Safe option, which does the same thing.
So I logged into a terminal server, which works. But I really didn't know what to do there. So what I did do was this

sudo apt-get install KDE

That worked. It installed KDE and when it was finished I simply logged into KDE. That's working fine. But I did notice that beryl-manager does NOT run automatically in KDE and if I do run it manually it does the same thing it does to Gnome.

This brings me to the conclusion that Beryl is freezing the system. So how do I uninstall beryl or disable it from starting with Gnome?


I tried searched but I couldn't find anything. Thanks!!!

---

### Post by Jason.TJ.Johnson on 2006-11-07
I figured it out!

I went into the gnome console and typed

```

sudo apt-get remove beryl-manager

```

I'm so damn proud of myself, lol. In the past whenever i had an issue like this I simply reinstalled Ubuntu, I'm trying to get away from that.

---

