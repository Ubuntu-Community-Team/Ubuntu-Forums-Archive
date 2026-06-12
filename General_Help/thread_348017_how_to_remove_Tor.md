---
title: "how to remove Tor"
date: 2007-01-28
forum: General Help
---

### Post by tomiu on 2007-01-28
I  can't deinstall Tor(i use ubuntu dapper)..i get this error:

```

* Stopping tor daemon (tor)...                                          [fail]
invoke-rc.d: initscript tor, action "stop" failed.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to stop Tor from terminal but i get this error:

```

Jan 28 12:37:03.527 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jan 28 12:37:03.532 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Jan 28 12:37:03.533 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 28 12:37:03.534 [err] init_from_config(): Acting on config options left us in a broken state. Dying.

```

---

### Post by JamieC on 2007-01-28
If it is non-graphical:-
```

sudo tor

```

If it is graphical:-

Gnome
```

gksudo tor

```

KDE
```

kdesu tor

```

---

### Post by Ramses de Norre on 2007-01-28
He wants to remove tor, not start it..
Have you tried running ```
sudo /etc/init.d/tor stop
``` before you removed it? (I don't have tor myself, it's possible that you have to capitalize the first letter or something..).

---

### Post by JamieC on 2007-01-28
> **Ramses de Norre said:**
> He wants to remove tor, not start it..
Have you tried running ```
sudo /etc/init.d/tor stop
``` before you removed it? (I don't have tor myself, it's possible that you have to capitalize the first letter or something..).

Sorry, I'm an idiot. I should've guessed from the dpkg errors...

---

### Post by tomiu on 2007-01-28
i tried:
```

sudo /etc/init.d/tor stop

```

and i got:

```

* Stopping tor daemon (tor)...                                          [fail]

```

:confused:

---

### Post by tomiu on 2007-01-29
ok i tried everything but still can't remove Tor..it runs in the background like daemon, KILL doesn't work too..any idea?

---

### Post by Kilz on 2007-01-29
> **tomiu said:**
> ok i tried everything but still can't remove Tor..it runs in the background like daemon, KILL doesn't work too..any idea?

you could try removing the package and restarting.

```
Jan 28 12:37:03.527 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jan 28 12:37:03.532 [warn] /var/lib/tor is not owned by this UID (1000). You must fix this to proceed.
Jan 28 12:37:03.533 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jan 28 12:37:03.534 [err] init_from_config(): Acting on config options left us in a broken state. **Dying.**
```

Also by the error you have shown, Tor isnt active

---

