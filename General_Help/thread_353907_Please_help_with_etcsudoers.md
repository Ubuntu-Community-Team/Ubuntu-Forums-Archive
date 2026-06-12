---
title: "Please help with /etc/sudoers"
date: 2007-02-05
forum: General Help
---

### Post by an.echte.trilingue on 2007-02-05
I am using Kubuntu 6.10 on a laptop with wireless.  My goal is to allow regular users to run wlassistant, among other things, as root, without having to enter a password.  I have been working on this for two days and I just can not make it work.

So, from what I gather, I need to add an entry to /etc/sudoers.  I cannot make this work.

This is what my /etc/sudoers file looks like right now:
```
#
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write an sudoers file
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults                    !lecture,tty_tickets,!fqdn


# User privilege specification
root        ALL=(ALL) ALL
# Allow user venla to use wireless
venla      ALL= NOPASSWD: /usr/bin/wlassistant

# Members of admin group may gain root privileges
%admin ALL=(ALL) ALL

```

I have tried every possible syntax for that wireless line that I can think of.  I have put it higher and lower in the file.  I have read the man page (which I still don't understand), searched google for hours.

What am I doing wrong?

Thanks
-mat

---

### Post by schilcha on 2007-02-05
I've had a hard struggle with sudo myself. Here's what works on my system (although I can't tell you, why your approach fails):
```

schilcha  smithers = NOPASSWD: /sbin/shutdown

```
where schilcha is my username and smithers is the hostname. 
--> in the line you try to grant permissions to user venla, substitute "ALL=" with "hostname=" .

Also, just to make sure to use "visudo" to edit the sudoers-file, DO NOT simply edit it with your favourite editor -- but you knew that already -- just to make sure...

Good Luck!

---

