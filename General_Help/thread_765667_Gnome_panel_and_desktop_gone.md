---
title: "Gnome panel and desktop gone"
date: 2008-04-24
forum: General Help
---

### Post by xaenyx on 2008-04-24
I just ran upgrades on hardy, and now everything's gone..  I logged out and logged back in, but the desktop icons are gone, the panels are gone, and though avant-window-navigator started, launching nautilus won't work.  I sudo su'ed and then tried

```
#apt-get install -f
```

didn't work, then

```
#apt-get install gnome
```

(unmet dependancy of gnome-desktop-environment)

```
#apt-get install gnome-desktop-environment
```

(depends on gnome-keyring-manager)

```
#apt-get install gnome-keyring-manager
```

(No such package)

```
#dpkg-reconfigure gnome
```

(no package installed)

```
#dpkg-reconfigure gnome-desktop-environment
```

(no package installed)


And archive.ubuntu is constantly screwing up/timing out/having packet loss.  Wtf is goin on?

---

### Post by xaenyx on 2008-04-24
halp D:

---

### Post by cnelson26 on 2008-04-30
Damn, I'm having basically the same problem.  Just upgraded to Hardy and now my panels aren't showing up.  It's weird, cuz they're actually there--like if i mouse over the clock, the tooltip for the clock appears--but everything is hidden.

I tried the terminal commands you had and got the same responses you did.  Have you had any luck with anything else?

---

### Post by cnelson26 on 2008-04-30
Just thought I'd let you know.  When I set advanced desktop effects to "None", everything instantly reappears.  So there is obviously something going on with this.  let me know if that was your problem too.

---

### Post by kaddy on 2008-05-01
Press alt+F2 and enter "gnome-panel" to get your panel back. Go to System>Preferences>Sessions and add gnome-panel to your session. That way, should your panel decide not to start on its own, your sessions file will tell it to.
[http://ubuntuforums.org/showthread.php?t=773499](http://ubuntuforums.org/showthread.php?t=773499)

---

