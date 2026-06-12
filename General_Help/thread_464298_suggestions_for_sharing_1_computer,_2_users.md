---
title: "suggestions for sharing 1 computer, 2 users?"
date: 2007-06-04
forum: General Help
---

### Post by bsmith1051 on 2007-06-04
My wife and I are trying to replace our old WinXP system with a new Ubuntu desktop.  But there doesn't seem to be anything comparable to XP's "Fast User Switching" feature on Ubuntu?  The new system has 2GB memory so it shouldn't be a problem running two 'separate' desktops on the one machine, but what's the best way to do this?

First of all, I'm assuming that we'll just use one Ubuntu user account.  I'm also assuming that we'll use the Workspaces feature to keep our open windows separate.

I've also succeeded in enabling the -ProfileManager feature in Firefox, so that it prompts for a user.   And it seems to then load a separate profile if you re-open it on the other workspace.  But is this ok?  I thought you could NOT run two copies of FF simultaneously?  

Any other suggestions?

---

### Post by Fireblend on 2007-06-04
Is the switch-user option not enough? Or are you talking about some other XP option I'm not aware of? I guess the assigning different desktops to a user is a good idea if you want to "switch" in less than a second, but then again it limits customization and you'll be stuck with only one background, set of desktop icons, etc...

---

### Post by Rui Pais on 2007-06-04
```
sudo apt-get install fast-user-switch-applet 
```


or add an extra graphical console (try first the applet)

---

### Post by steeleyuk on 2007-06-04
I would have thought it would be simpler to create two user accounts, then switch using the User Switcher. Works in a similar way to Windows XP...

---

### Post by bsmith1051 on 2007-06-05
bah!  My mistake, I didn't realize there was such a function.  I'd tried searching for "shared desktop" but not on "fast user switch" so I'd failed to find anything about it.

It looks like the key to making this easy is:
1. install applet
 > sudo apt-get install fast-user-switch-applet
2. right-click on desktop Panel (bar across the top of the screen)
3. select Add To Panel > Miscellaneous / User Switcher, then Add, then Close

---

### Post by Rui Pais on 2007-06-06
> **bsmith1051 said:**
> bah!  My mistake, I didn't realize there was such a function.  I'd tried searching for "shared desktop" but not on "fast user switch" so I'd failed to find anything about it.

It looks like the key to making this easy is:
1. install applet
 > sudo apt-get install fast-user-switch-applet
2. right-click on desktop Panel (bar across the top of the screen)
3. select Add To Panel > Miscellaneous / User Switcher, then Add, then Close

Yes. 
Another way to get more or less the same (may takes a little more resources, but i find it easier and my users -one of them my kid with 6 - find it more intuitive and simpler) is just add:
```
1=Standard
```
to section [servers] of /etc/X11/gdm/gdm.conf-custom and restart X server.

That way besides the usual graphical console on F7, X server will start another one at F9 (F8 on dapper or old), so we log/change sessions pressing Ctrl+Alt+F7/Ctrl+Alt+F9. 
:)

---

### Post by zvacet on 2007-06-06
I will go with steeleyuk advice.

---

