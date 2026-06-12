---
title: "[SOLVED] Possible to launch script on login of all accounts?"
date: 2008-01-10
forum: General Help
---

### Post by GumbyX on 2008-01-10
I know this is an odd question, but its something I need to have done on a few computers at work. 

I have been asked to display a message on-screen whenever a user logs into the system. I found a way to get the message displayed (gmessage) and have a script added to root's session menu to run it. It does work  but I need this message to display for all current and future users accounts. Is there someway to do this? I have tried messing with .profile, rc.local, and a number of other things that I found while searching for an answer. The problem with these is that it runs the script on boot-up, not user log-in. 

I was told by someone I work with that there is a universal/default startup program list in Ubuntu, but he can't remember where it is. If anyone can help me out, I would appreciate it.

---

### Post by forestpixie on 2008-01-10
he might be talking about sessions - in system preferences

it's where I put things to start on login

I assume there are seperate ones for each user, but can't be sure as I only have 1 user

Edit - ok added a user logged in as new one and get new default sessions - so I assume you could do it that way if there's not many to do as each would need to be done seperately.

I'll be interested to know the answer to this

---

### Post by Vixis on 2008-01-10
try to put script in
> /etc/rcS.d/
see /etc/rcS.d/README for details

---

### Post by forestpixie on 2008-01-10
would that not only work when booting - rather than when logging in which is what op is after

---

### Post by MartynA on 2008-01-10
Hmm, would it be possible to add some lines to .profile file in the users home directory?

To do it for all future users add it to the .profile in /etc/skel/ 

Would they be executed.

---

### Post by heindsight on 2008-01-10
you could put any commands that you want executed every time any user logs in to an xsession
via gdm into /etc/xprofile

for example if /etc/xprofile looks like:
```
#!/bin/sh

xmessage -file /etc/motd -center
```
Then everytime any user logs in to an x session (via gdm) a message containing the text from /etc/motd
will be displayed in the center of the screen.

You could also add commands /etc/profile, but that would also gets executed when users start
a (bash) login session from a terminal so you'd have to also include tests to see whether
the user is login into a terminal or an X session.

The problem with putting such commands in /etc/skel/.profile is that it will only apply to users
created after the the changes made in /etc/skel and the user will be able to disable it.

You could also add commands to /usr/share/gnome/default.session, but this has the same
drawbacks as using /etc/skel/.profile.

Putting a script in /etc/rcS.d will cause the script to run ONCE, fairly early in the boot sequence
not every time a user logs in.

---

### Post by MartynA on 2008-01-10
Will remember this for future reference, thanks.

---

### Post by GumbyX on 2008-01-11
Thanks heindsight. It worked perfectly. You saved me a lot of wasted time.

---

