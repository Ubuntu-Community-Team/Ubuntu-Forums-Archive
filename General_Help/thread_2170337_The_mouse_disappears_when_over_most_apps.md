---
title: "The mouse disappears when over most apps"
date: 2013-08-25
forum: General Help
---

### Post by wiseguy12851 on 2013-08-25
I'm running Ubuntu 13.04 64-bit, after I installed ubuntu I installed quite a number of packages (Several Gigabytes worth), when I restarted I found that the mouse cursor was invisible, when I opened up firefox I could see it normally but as soon as I moved it off firefox it vanished. I tried several other programs but it acts the same.

Finally I went to the extreme and deleted all . folders and moved most all of the . files to a Backup folder except for .bashrc .profile and the like but it's having the same problems.

---

### Post by stinkeye on 2013-08-25
Try putting mouse settings back to default....
```
gsettings reset org.gnome.desktop.interface cursor-theme
gsettings reset org.gnome.desktop.interface cursor-size
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/DMZ-White/cursor.theme 100
```
Log out/in

---

### Post by wiseguy12851 on 2013-08-26
It didn't fix the problem

---

### Post by stinkeye on 2013-08-26
> **wiseguy12851 said:**
> It didn't fix the problem

Try creating a new user and see if it exists in that login.

---

### Post by wiseguy12851 on 2013-08-26
Sorry for late reply, I went through a lot of trial and error trying to create another user to see if problem exists there, to sum up:

1) Logged into my account in the Ubuntu Session and created 2nd user, logged out but the user wasnt there, tried other means including terminal but system acted like it was never created, tried to go back to original account but system would let me and restart button wasn't working in display manager so had to ctrl + alt + f1 and reboot entire system from there
2) Logged into my account in the XFCE Session and tried again creating user, logged out and the username appeared this time but the session box was grayed out, I logged in anyways and it took me to some after step session where the mouse was again invisible, I logged out of after step session and the session box became ungrayed out so I chose Ubuntu as the session but it complained I was logged in when I wasn't (I double checked), so I tried logging back into my old account but the session box was grayed out so I tried restarting but the restart button wouldn't work so I had to ctrl + alt + f1 and sudo reboot again from there.

So I never got a chance to test the mouse in Ubuntu.

Also:

a) It appears that the KDE Session doesn't work at all but takes to a solid non-interactive black screen but the mouse works normally
b) Once you log out from anything you have to restart from ctrl + alt + f1 as theres no way to log back in, it thinks your still logged in when your not and other users aren't able to login at all anymore
c) The mouse works normally on XFCE but some programs like Qt Creator and some others it's invisible
d) Ubuntu has frequent crashes on seemingly random programs when you are able to log into it
e) New accounts are stuck in After Step session as the session box is grayed out
f) The buttons on the login manager don't work after you've logged in at least once
g) Essentially the only thing that works 100% of the time is the real console on the ctrl + alt + f1-6 keys, everything else is very unstable

---

### Post by stinkeye on 2013-08-26
Yeah, I don't like to mix too many desktop sessions.
They don't seem to play nicely these days.
Was the original problem in all sessions?
I have had problems recently with mouse flickering in an xfce session.Seems ok now.

I have Ubuntu 13.04 with fallback and xfce sessions  installed with "load gnome services at startup" enabled in  the xfce session manager.
Did you enable any extra ppa's.

---

### Post by wiseguy12851 on 2013-08-26
I have about roughly 25 or so sessions installed along with a ton of window managers compiz stuff and all the major and some minor meta packages along with a ton of other plugins, extensions, etc...

Yes, from what I can grasp the problem is in all sessions but it doesn't seem to be as simple as the session itself but more like a chain of packages that aren't playing nicely with each other and are causing a lot of problems on the overall system, it's programs, and services. That's only a guess though.

No I haven't had a problem with flickering in xfce and I've checked ubuntu and kubuntu services to be start up at login.

About the only place the mouse works consistently is the login page.

---

### Post by stinkeye on 2013-08-26
I don't know what else to try.
The only other thing to do with the mouse I know is the ~/.Xresources file which
can alter mouse settings like cursor size.

---

### Post by wiseguy12851 on 2013-08-26
Thanks for trying

---

