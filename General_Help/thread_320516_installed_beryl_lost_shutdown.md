---
title: "installed beryl lost shutdown"
date: 2006-12-17
forum: General Help
---

### Post by jswan on 2006-12-17
after installing beryl-xgl, my xgl desktop doesn't have restart or shutdown in the power menu.   
the only options i have are
log out
lock screen
switch users
suspend hibernate

but all the options still appear on my gnome desktop

how do i get these extra options back??

cheers ~james

---

### Post by bulldog on 2006-12-17
Go to System->Administration->Login screen and check the action menu on the first tab.

---

### Post by Azakus on 2006-12-17
XGL does that because by default, Ubuntu only gives you those options on Screen 0, the first screen. XGL uses Screen 1 to render effects, which gets rid of those options. If no option works, get rid of XGL and try Beryl on AIGLX (built into Ubuntu and easy used the nvidia 1.09XX drivers)

---

### Post by jswan on 2006-12-17
to be more specific its the logout button i'm having troubles with
all these options work:
log out
lock screen
switch users
suspend hibernate

but there is no buttons for:
shutdown
restart

currently to restart i have to logout and hit the restart or shutdown from the login screen

its a minor hassle but i'm assuming fixable

---

### Post by styven on 2006-12-18
I am having the same issue, no beryl though.
i can't even shut down from the sign in screen, i have to use the power button on the laptop, not sure this is healthy for the hdd long term.
Every thing was fine on fresh install, problems started after updates were actioned.

Edgy on HPnx6310 laptop.

Steve

---

### Post by Azakus on 2006-12-18
> **styven said:**
> I am having the same issue, no beryl though.
i can't even shut down from the sign in screen, i have to use the power button on the laptop, not sure this is healthy for the hdd long term.
Every thing was fine on fresh install, problems started after updates were actioned.

Edgy on HPnx6310 laptop.

Steve

You can always do this. In a terminal window type this code
```
sudo shutdown -h now
```
This will shutdown the computer the full and correct way, just with no graphical button to do it for you.

---

### Post by wpshooter on 2006-12-18
> **jswan said:**
> after installing beryl-xgl, my xgl desktop doesn't have restart or shutdown in the power menu.   
the only options i have are
log out
lock screen
switch users
suspend hibernate

but all the options still appear on my gnome desktop

how do i get these extra options back??

cheers ~james

Seem like to me that I read a similar post this morning where someone was having this same problem.

Maybe you can find that post and see if they found a resolution.

Good luck.

---

### Post by tari on 2006-12-18
I've got that, too, with beryl and xgl.  You could just add a panel application launcher or menu item to shutdown: just have it run
```

gksudo shutdown -h now

```

---

### Post by DJ_Peng on 2006-12-24
> **Azakus said:**
> XGL does that because by default, Ubuntu only gives you those options on Screen 0, the first screen. XGL uses Screen 1 to render effects, which gets rid of those options. If no option works, get rid of XGL and try Beryl on AIGLX (built into Ubuntu and easy used the nvidia 1.09XX drivers)

I made the mistake of installing XGL when I was adding Beryl and now I want to go with AIGXL. My video card is an Nvidia NV11DDR (GeForece2 MX 10 /DDR/200DDR) and I'm using the Nvidia drivers (not sure if it's the 1.09XX drivers, but I do know it's not the legacy drivers). What would be the best way to ditch XGL and go with AIGXL? I too want my original logoff options with shutdown and restart.

---

### Post by PrinceArithon on 2006-12-24
gksudo shutdown -h now


Seriously??  I never heard of this command before.  I just now seen it and didn't try it.

If that doesn't work...even though it seems it should...you could always type this command in the terminal

sudo init 0


init 0 is the command I learned years ago when working with Redhat 7.3

---

### Post by dbd on 2007-01-16
Does anyone know what the commands are for suspending?

---

