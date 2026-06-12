---
title: "Login in to a login screen..."
date: 2007-04-10
forum: General Help
---

### Post by flipjarg on 2007-04-10
Today Kubuntu began logging into a login screen. i login with the correct password (an invalid password brings up a message) and it looks like it's going to login to KDE. The screen goes black and my mouse turns into a watch then a regular mouse cursor. But instead of KDE starting up it goes back to the login screen. Does anyone have any ideas?

i've already reinstalled Kubuntu. i do have a separate 'home' partition though. So it has to be a problem with some application or some settings i'd think.

The other thing i've tried is running 'dpkg-reconfigure xserver-xorg' again no go. And there are no 'nvidia' drivers to choose, only 'nv'.

Thanks for the help :-)

---

### Post by mac.ryan on 2007-04-10
Today I read of a kubuntu user having a similar issue.
Pressing CTRL-ALT-F7 - though - brought her to the normal Desktop environment. Does this work for you?

---

### Post by flipjarg on 2007-04-10
Well, hitting ALT+CTRL+F7 is what i'm already at. But when i hit ALT+CTRL+F7 it brings me to a text mode login which i CAN login to successfully. When i go back to ALT+CTRL+F7 it still acts the same.

---

### Post by mac.ryan on 2007-04-10
So it looks that the X session doesn't get kicked off at all. Does it helps doing:

```
startx
```

?

---

### Post by flipjarg on 2007-04-10
i just tried it and it gave me this:> Server already active for display 0
...
No such process (errno 3): Server error.

i tried just hitting 'X' today but it gave me the same thing. Just so you know X is already running (and it acts normal) when i am brought to the graphical login.

---

### Post by mac.ryan on 2007-04-10
So, if you are 100% your X server "acts normally", this leaves the option open only for a kde problem, then.

I run gnome and not kde. Under gnome I would recommend to try move the .gnome2 config files into another directory and see if this allows you to get into the GUI (without your tweaks, though). Then you could bring back individual config files one by one and see what is the one who stops the show...

Maybe you can try the equivalent under kde... (?)

---

### Post by dreadlord_chris on 2007-04-11
> **flipjarg said:**
> Today Kubuntu began logging into a login screen. i login with the correct password (an invalid password brings up a message) and it looks like it's going to login to KDE. The screen goes black and my mouse turns into a watch then a regular mouse cursor. But instead of KDE starting up it goes back to the login screen. Does anyone have any ideas?

i've already reinstalled Kubuntu. i do have a separate 'home' partition though. So it has to be a problem with some application or some settings i'd think.

The other thing i've tried is running 'dpkg-reconfigure xserver-xorg' again no go. And there are no 'nvidia' drivers to choose, only 'nv'.

Thanks for the help :-)

Did you just re-install Kubuntu when this started happening? If so there's a good chance that when you re-mounted your old Home partition the UIDs & GUIDs are different then your new current UID & GUID. You can check this easily by choosing System > Console log in from the Login screen. Log into your account then enter:
```

ls -la

```
Look in the 3rd & 4th columns - you user name should be listed in both. If your account's UID & GUID have changed you will see question marks (?) in most of both columns. Basically, everything in your home folder & sub folders *should* be owned by you. If not enter this:
```

sudo chown -hR <NAME>:<NAME> /home/<NAME>

```
Replace <NAME> with your user name. This will (re)set the permissions on everything in you home on down to you.

If you can't log in to the console from your account then boot into recovery mode. In this case change the following commands:
```

ls -la /home/<NAME>

```
and
```

chown -hR <NAME>:<NAME> /home/<NAME>

```

HTH

---

### Post by Inw on 2007-07-23
Hi, i'm having the same problem, and when i tried what you said i found that everything is owned by root. I couldn't change it though. Can you please help?

---

### Post by dreadlord_chris on 2007-07-23
> **Inw said:**
> Hi, i'm having the same problem, and when i tried what you said i found that everything is owned by root. I couldn't change it though. Can you please help?

yup.... just sudo that chown command:
```

sudo chown -hR <NAME>:<NAME> /home/<NAME>

```

---

