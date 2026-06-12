---
title: "slow-keys on despite &quot;accessability features&quot; disabled"
date: 2012-10-25
forum: General Help
---

### Post by Mozai on 2012-10-25
I encountered a problem since upgrading to Ubuntu 12.10, where the 'Slow-Keys' feature would detect and turn on from holding the shift-key down for too long... but could not be turned off the same way.

I checked `xfce4-settings-manager` under "Accessability", and "[ ] Enable assistive technologies" was turned off, as well as "[ ] Use sticky keys" and "[ ] use slow keys".  I hit the interweb series of tubes, where I found many people telling me I had to edit settings in gconf and it must be because I accidentally turned it on in GNOME.  .... except I don't have GNOME installed.

I did find one thoughtful person who reported this problem to the Fedora Project in January 2012.  That group discovered the problem was not with GNOME nor xfce, but with X.Org itself, as somewhere upstream the 'Accessability Features (AccessX)' default setting was flipped to be on by default.  Turning it off in the X.Org server seems to fix the problem.

**TL;DR: if Slow-Keys turns on despite you not enabling it:**
```
sudo aptitude install xkbset
xkbset -sl # turns off Slow-Keys 
xkbset -a  # turns off Acessability Features so Slow-Keys won't turn on again
```

To do this each time you start a new X session, I believe it should be enough to add these lines to $HOME/.xsessionrc
```
# turn off 'Accessability'; on by default since ubuntu 12.10
/usr/bin/xkbset -a
# turn off 'Slow-Keys'; on by default since ubuntu 12.10
/usr/bin/xkbset -sl
```

The relevant bug report in Fedora Core is [#816764 (Jun 2012)]("https://bugzilla.redhat.com/show_bug.cgi?id=816764") but the comments are damnably confusing because people keep insisting it's a problem with GNOME, despite being proven multiple times it's affecting systems where GNOME is not installed.

---

