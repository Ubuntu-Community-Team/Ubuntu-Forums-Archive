---
title: "[help] Start a program with X?"
date: 2005-10-31
forum: General Help
---

### Post by theclaw on 2005-10-31
I've been using [synergy](http://synergy2.sourceforge.net) on my laptop and desktop and it's great. I highly recommend this.

I put this in my ~/.kde/Autostart directory and it also works great, having the synergy client connect only if I'm connected to my own AP.

```

#!/bin/bash
#synergy.sh
if [ -n "$(iwconfig eth1 | grep <mac address>)" ]; then
 /usr/bin/killall synergyc
 sleep 1
 synergyc <ip>
fi

```

I would like to put a line somewhere to run this script also when X starts so I can use synergy for logging into my laptop. I've looked into a .xinitrc file, but there isn't one already so I don't know if ubuntu uses them.

Thanks in advance.

---

### Post by theclaw on 2005-11-02
Oh, I was hoping someone would know. I guess I'll post here when I figure it out for other people who are searching for an answer.

---

### Post by shinygerbil on 2005-11-02
there's a way of adding it to /etc/init.d, using the command update-rc, because I managed to stumble across it when trying to get a script for wireless connection to run on startup, but a quick search of the forums again reveals nothing... *tries to retrace steps*

Steve

P.S. Love the avatar :P

---

### Post by shinygerbil on 2005-11-02
Ok, it seems you can put the script/command into the startup using 'sudo update-rc.d {scriptname} defaults' but you may need to tweak the defaults. I'm not too good on the startup sequence, what runlevels you'd need to put it in, but basically that's how you get something to run at bootup.

If I find anything else, I'll let you know, but as I don't use Synergy I doubt I'll ever find anything that's directly relevant, if you know what I mean.

Oh and [this](http://www.debian-administration.org/articles/28) page can tell you more about update-rc.d, but not much. As it says, you're better off doing 'man update-rc.d'

Hope you get somewhere with this

Steve

---

### Post by theclaw on 2005-11-03
Thanks. I'll look into it!

---

### Post by theclaw on 2005-11-11
Ok, here's how you do it!

in /etc/kde3/kdm (assuming you're using KDM for your login) there are several files

Xsetup - run as root before the login dialog appears
Xstartup - run as root before session starts
Xreset - run as root after session exits

amongst others...

What you want to do is add
```

exec /path/to/synergy.sh

```

To Xsetup in order to have synergy on on the login screen and to Xstartup to have it run automatically when the session starts.

It might be better to add something in there to chown of the process to the user, but that's optional.

Hopefully this will help others. Credit goes to CapnBry on the SA forums for telling me.

---

