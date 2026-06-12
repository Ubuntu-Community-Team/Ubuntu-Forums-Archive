---
title: "Cannot login normally, only Gnome Failsafe"
date: 2007-09-12
forum: General Help
---

### Post by matrooswolf on 2007-09-12
Hi,
I cannot login normally anymore.
I think I messed up my sessions.

When I login I get sound, and the banner with metacity but everything freezes there.  I can move my mouse, when I click the banner disappears leaving me a blank screen (ubuntubrown).  I have to CTRL-ALT-Backspace to get out.

I can login with session Gnome Failsafe
Then everything appears to work normally.  Compiz is running on startup (Fusion-icon is one of the startup scripts).  I can switch between Compiz and Metacity.

I never quite understood sessions, so forgive me if it is a stupid question, but how do I get this failsafe session (that appears to works) to be my default session next time I startup?
And isn't the failsafe session  supposed not to run startup scripts like Fusion-icon? (it does) 

And generally, anybody any idea what could be wrong with my system, or where I would have to start looking?

Any help to get me back to sanity greatly appreciated!

some more info:
- system completely updated
- 1GB ram
- AMD 3000+
- running compiz fusion with nvidia 100.14.11
I have recently added this line to Xorg.conf (to be able to set the refresh rate):
Option "DynamicTwinView" "FALSE" Option

---

### Post by prince_niceguy on 2007-09-13
did you install beryl or compiz that it got messed up???

---

### Post by matrooswolf on 2007-09-16
Hi, 

I read a lot about sessions,
First tried to remove ./gnome/session, but I didn't have that file.

So I read about saving the session and making it the default session with the command:
I did ALT+F2 and then
```
gnome-session-save
```
hoping that would save my working failsafe  session to a default session, but it didn't work (actually the command worked, but restarting didn't)

So I found the file
```
/usr/share/gnome/default.session
```
I opened it and copied and pasted it into
```
 ./gnome/session

```
et voilà, everything works fine as before

---

### Post by Endolith on 2007-12-14
> **matrooswolf said:**
> 
So I found the file
```
/usr/share/gnome/default.session
```
I opened it and copied and pasted it into
```
 ./gnome/session

```
et voilà, everything works fine as before

It's ~/.gnome2/session, and renaming that file has the same effect.

---

