---
title: "Remove pop-up after selecting 'Try Ubuntu'"
date: 2020-02-20
forum: General Help
---

### Post by sampsonats on 2020-02-20
I'm using Cubic to master my own bootable USB stick. When I boot the USB stick and select 'Try Ubuntu', a window pops up to tell me about features of Ubuntu and makes me click 'next', 'next', .. 'done'. I'm using this a lot and I don't want this window to pop up any more.

How can I make it so this window never pops up?

Thanks,
Todd

---

### Post by Bashing-om on 2020-02-20
sampsonats; Hello -

I have no familiarity with cubic - so take with that grain of salt.
Ubuntu has that feature as "ubiquity-slideshow-ubuntu" that in the remaster can be removed.
see:
```

apt show ubiquity-slideshow-ubuntu

```
in terminal.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2020-02-20
Along with Bashing-om's advice, and if I'm not mis-understanding.

The welcome screen is part of the "gnome-initial-setup" package. The first time a user logs into a new machine the command** " /usr/lib/gnome-initial-setup/gnome-initial-setup"** --exisiting-user runs.
for myself simply removing the gnome-initial-setup package during kickstart was a suitable fix.
EDIT: If you would like another method, you can also edit** "/etc/gdm/custom.conf"** and add this to the bottom:
```

[daemon]
InitialSetupEnable=false
```
Example of mine:
```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

[B][daemon]
InitialSetupEnable=false[/B]

```

---

### Post by sampsonats on 2020-02-21
I did: sudo apt remove --purge [COLOR=#000000][FONT=&quot]ubiquity-slideshow-ubuntu

That did the trick.  There was no [/FONT][/COLOR]**/etc/gdm/custom.conf **file.

Thanks!!!

---

### Post by Bashing-om on 2020-02-21
sampsonats; -

Good deal :)

As you have a solution -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]all in some understanding :)[/INDENT]

---

