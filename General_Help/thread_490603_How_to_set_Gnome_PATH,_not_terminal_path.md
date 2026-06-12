---
title: "How to set Gnome PATH, not terminal path?"
date: 2007-07-02
forum: General Help
---

### Post by therealbrewer on 2007-07-02
I want to set the system-wide PATH so that all programs, even those run from a panel in Gnome, can access a certain directory. I don't want to edit .bashrc since that PATH would only be seen by programs launched from a terminal.

I put these lines into my ~/.profile assuming that it would be executed when I boot into Gnome:

```
source /opt/intel/fc/10.0.025/bin/ifortvars.sh
source /opt/intel/idb/10.0.025/bin/idbvars.sh
```

These are just some scripts provided with the Intel Fortran compiler.

However, after rebooting, or restarting Gnome with ctrl-alt-backspace, the PATH is not updated.

Interestingly. if I do

```
source ~/.profile
```

from a terminal, then the terminal PATH is updated, so ~/.profile is clearly calling the scripts correctly, but it seems that ~/.profile is not being executed when I login to Gnome. I know that ~/.profile is not read if ~/.bash_profile or ~/.bash_login exist, but in this case they don't.

And it gets even stranger still. If I put the scripts into /etc/profile instead of ~/.profile, they still don't get executed! Isn't /etc/profile supposed to be executed for all users no matter what?!?!

One last weirdness: If I switch out of Gnome with ctrl-alt-F1, then login to the full-screen terminal, then the path IS updated!! This makes me believe that the problem has something to do with Gnome not being a "login shell", or some such thing, but I don't know much about shells...

Can anyone enlighten me?

By the way, this is on a fresh install of Feisty. Oh yeah, one more thing, the method above (scripts in ~/.profile) works without a hiccup on another machine! Is there any way to trace the startup sequence? Any place to look for error messages?

HELP PLEASE!

---

### Post by therealbrewer on 2007-07-02
Well, I figured it out by myself...

I had to change this

```
source /opt/intel/fc/10.0.025/bin/ifortvars.sh
source /opt/intel/idb/10.0.025/bin/idbvars.sh
```

to this

```
. /opt/intel/fc/10.0.025/bin/ifortvars.sh
. /opt/intel/idb/10.0.025/bin/idbvars.sh
```

Don't know why...

---

