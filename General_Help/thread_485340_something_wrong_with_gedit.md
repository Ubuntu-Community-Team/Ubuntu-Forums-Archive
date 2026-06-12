---
title: "something wrong with gedit?"
date: 2007-06-26
forum: General Help
---

### Post by TonySmash on 2007-06-26
something's up with gedit, and it has me worried...

```
tony@ubuntu:~$ gksudo gedit /etc/apt/sources.list

***MEMORY-WARNING***: gksudo[6236]: GSlice: g_thread_init() must be called before all other GLib functions; memory corruption due to late invocation of g_thread_init() has been detected; this program is likely to crash, leak or unexpectedly abort soon...

(gedit:6237): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...
```

anyone have anything similar? whats going on here?

---

### Post by AlexThomson_NZ on 2007-06-27
Doesn't fail for me using exactly the same command.

I'm using gedit 2.18.1 and Feisty.

Some more info would be nice- does it only fail using this command? or any command? or only as root?

Looks more like a problem with gksudo, causing a flow-on problem for gedit.

Does gksudo fail with any other programs?

---

### Post by Patrick-Ruff on 2007-06-27
I generally just run the command with sudo, rahter then gksudo. not sure if it makes any difference, as they are the same command.  

yeah, Gnome UI warning, that MUST be gksudo.  use normal sudo and it should work.

---

### Post by AlexThomson_NZ on 2007-06-27
> **Patrick-Ruff said:**
> I generally just run the command with sudo, rahter then gksudo. not sure if it makes any difference, as they are the same command.  

yeah, Gnome UI warning, that MUST be gksudo.  use normal sudo and it should work.

True- why are you using gksudo on the command line anyways?

well spotted Patrick :)

---

### Post by merlinus on 2007-06-27
FWIW, gksudo is preferred for running graphical apps from a terminal.  There are documented problems with using sudo for this.

-merlin

---

### Post by AlexThomson_NZ on 2007-06-27
I'm interested to hear that- I always though gksudo existed only to allow users to enter a password when stdout was unavailable.  What kind of probs does sudo cause, and I'll do some googling... :)

---

### Post by FuturePilot on 2007-06-27
Using sudo on graphical apps will mess up your permissions
Look here
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by TonySmash on 2007-06-27
no worries guys, thanks for the help though!! i prefer using nano for editing from the terminal anyway :)

---

### Post by AlexThomson_NZ on 2007-06-27
> **FuturePilot said:**
> Using sudo on graphical apps will mess up your permissions
Look here
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

Cheers for the heads-up!  Will have to try to break the habit...

---

