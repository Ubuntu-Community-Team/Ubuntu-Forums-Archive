---
title: "Shutdown during installations"
date: 2007-06-18
forum: General Help
---

### Post by Amackera on 2007-06-18
Hey everyone. Here's my dilemma:

Whenever I try to run the ./configure script included with Qt, my computer will reach a point and shut itself down for seemingly no reason. I can't tell if it's writing anything to the console, because it exists out of the DE too fast.

It exits my DE (Gnome), and kicks me down to a CLI with a few lines on it. They read:

```
 
... Random stuff that I can't remember ... 

Something about apache server shutting down.

Checking battery state      [OK]

Running local scripts /etc/rc.local

```

Or something along those lines. I could copy them all down but they look to me like standard shutdown prompts. And my /etc/rc.local looks like this:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```
Which is hardly helpful at all!

Also, this doesn't just occur with the configure script for Qt. It happens whenever I run a configure script, or try to compile or install a program (but packages from synaptic work fine). Any thoughts?

---

### Post by malfist on 2007-06-18
the rc.local file is a script that is ran every time the computer is booted up, I've used it for stuff like ifup wlan0 or stuff like that, it has root access too.

---

### Post by Amackera on 2007-06-19
As an update: I think it has something to do with temperature. I modified my cooling apparatus and the script was executed without a hitch.

So.. what's Ubuntu's method of dealing with cooling issues? If the processor overheats does it just power down? I'll do some digging, see what I can find.

---

