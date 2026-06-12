---
title: "password lost/changed after upgrade!"
date: 2007-01-10
forum: General Help
---

### Post by stewacide on 2007-01-10
After routinely installing the latest Edgy updates and restarting as directed suddenly Ubuntu tells me my user password is wrong! I can log in to gnome because I have the system set up to auto-log-in, but I can't do anything that requires a password. Whether I attempt to enter it from the GUI or the command line, or I attempt to connect to the computer remotely, it's saying my password (which has been the same for years! have never made any attempt to change it!) is incorrect?!?

This isn't something silly like having the capslock key on, because I have the password and login name saved on other computers to automatically connect to file shares, and they're getting the same message that the password is suddenly wrong.

WHAT ON EARTH could this be? And HOW CAN I FIX IT!!! This seems like a MAJOR, KILLER bug to me, whatever is causing it.

---

### Post by taurus on 2007-01-10
Boot into recovery mode from GRUB menu and at the prompt, change your password, assuming **stewacide** is your username.

```
passwd **stewacide**
shtudown -r now
```

---

### Post by stewacide on 2007-01-10
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, change your password, assuming **stewacide** is your username.

```
passwd **stewacide**
shtudown -r now
```

Are there any nasty side-effects to doing this? Otherwise thanx a million.

---

### Post by Delkster on 2007-01-10
> **stewacide said:**
> Are there any nasty side-effects to doing this? Otherwise thanx a million.

Shouldn't be -- it just changes your password to whatever you tell it to.

The latter command is 'shutdown', though.

In any case, I'd definitely be interested in knowing what on earth has changed your password if that's what really has happened. Updates usually don't touch such configuration files like the one where the user and password information is stored. Did you happen to pay attention to what packages were upgraded?

---

### Post by stewacide on 2007-01-10
> **Delkster said:**
> Shouldn't be -- it just changes your password to whatever you tell it to.

The latter command is 'shutdown', though.

In any case, I'd definitely be interested in knowing what on earth has changed your password if that's what really has happened. Updates usually don't touch such configuration files like the one where the user and password information is stored. Did you happen to pay attention to what packages were upgraded?

The major one (that forced the re-start) was the latest xorg driver I believe. I didn't pay attention to the others, but I tend to update weekly or so, so something recent.

What files would I be looking for the update to touch that would change the password?

I'm accessing the system remotely (I have passwordless-VNC set up: yeah, I'm very security minded ;)) so I won't be able to tell until I get to the machine and reset the password. I'll be sure to file a bug report when I do.

---

