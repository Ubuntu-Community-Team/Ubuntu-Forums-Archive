---
title: "Ubuntu 16.04 Automatically Turn On Numlock After Login"
date: 2016-05-11
forum: General Help
---

### Post by wewantutopia on 2016-05-11
The official Ubuntu documentation is no longer valid as far as I can tell.   System Settings > Keyboard Layout > Options > Miscellaneous,  Check "Default numeric keypad keys".

Can someone tell me how to do it now?  Thank you!

---

### Post by wewantutopia on 2016-05-18
Bump.  Thanks!!

---

### Post by leunam12 on 2016-05-18
install numlockx and set it to run at startup like this:
```
numlockx on
```
Check also the link below...
[http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/06/turn-on-numlock-ubuntu-14-04/)

---

### Post by Impavidus on 2016-05-18
I'm not sure about Ubuntu, but in Xubuntu there's an option under keyboard settings to restore numlock status at startup, which, I assume, means it will be set to the same as it was at shutdown.

---

### Post by scdragos on 2016-05-22
gksu gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu-mate.conf

and add: greeter-setup-script=/usr/bin/numlockx on

It should look like this:

[Seat:*]
user-session=mate
allow-guest=false
greeter-setup-script=/usr/bin/numlockx on

If, before the shut down, num lock is on, after logging will still be on.

---

### Post by jim_deadlock on 2016-05-22
Numlock setting is often found in the BIOS

---

### Post by pqwoerituytrueiwoq on 2016-05-22
> **jim_deadlock said:**
> Numlock setting is often found in the BIOS
and it normally gets turned off by the time lightdm loads

```
~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
[B]greeter-setup-script=/usr/bin/numlockx on
session-setup-script=/usr/bin/numlockx on[/B]
```

---

### Post by wewantutopia on 2016-05-25
Thanks for all the replies!  

I have added the lines

```
[B]greeter-setup-script=/usr/bin/numlockx on 
[/B]**session-setup-script=/usr/bin/numlockx on**
```

to both /etc/lightdm/lightdm.conf and /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf (I'm not using Mate) with no luck.  I have, of course, installed numlockx too.

I have been making sure that numlock is on before I power off the machine.

I've had, and still have on a different partition, 14.04 on this computer for years with no numlock issues.

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2016-05-25
what flavor are you using?
maybe you are not even using lightdm
i think ubuntu gnome uses gdm and cinnamon (one of linux mint's DE choices) might

---

### Post by jim_deadlock on 2016-05-25
Yes Ubuntu Gnome = gdm

---

### Post by wewantutopia on 2016-05-25
Oops,  sorry.   Vanilla Ubuntu 64 bit with Unity 7

---

