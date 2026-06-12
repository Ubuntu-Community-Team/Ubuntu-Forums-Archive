---
title: "[SOLVED] pidgin broke after upgrade to gutsy"
date: 2007-10-18
forum: General Help
---

### Post by cnkbrown on 2007-10-18
I manually installed pidgin 2.2.0  under feisty. After upgrade to gutsy pidgin won't connect to my jabber server - it displays a message "SSL support unavailable."

Any suggestions?

---

### Post by orbital on 2007-10-18
I have the same problem with my MSN account:

"SSL support is needed for MSN. Please install a supported SSL library."

I also installed it manually. Any help?

---

### Post by orbital on 2007-10-19
I just uninstalled the manual one using ./configure and sudo make uninstall

Pidgin works fine now.

---

### Post by warpedreality on 2007-10-19
> **orbital said:**
> I just uninstalled the manual one using ./configure and sudo make uninstall

Pidgin works fine now.

Clearer instructions would help the Gutsy n00bs please :D Thanks!

---

### Post by FredB on 2007-10-19
In a console, this person goes into the pidgin source directory.

After that, that person entered :

```
./configure
sudo make uninstall
```

First line : configure source code before building
Second line : remove previously installed by hand version.

Hope it is clearer.

---

### Post by cnkbrown on 2007-10-19
The casual user is reading that last post and wondering, "How can it work if he uninstalled it?"

I poked around in synaptic and found the gutsy upgrade installed pidgin 2.2.1, apparently in some location that didn't conflict with my manual installation of 2.2.0.

I tried removing the ubuntu pidgin, and re-installing the manual pidgin - but that still had the ssl problem.

Next, I uninstalled the manual pidgin and  re-installed the ubuntu version.  Now, it appears to have wiped all my buddy information --or-- it has silently failed to connect to the server - I'm not sure which.

---

### Post by cnkbrown on 2007-10-19
I've determined that the ubuntu flavor of pidgin is brain dead - it won't connect to the server, and when I try to add a new account, the "Protocol" pulldown is empty, so I can't specify 'jabber' - or any other IM protocol for that matter.

I did google one other thread (can't find it at the moment) talking about pidgin in the gutsy beta.  Their solution was to wipe the disk and do a clean install.  Now what does that remind me of?

I'm back to my original post - how do I get my old pidgin install some ssl support?

---

### Post by Roobert on 2007-10-19
> **orbital said:**
> I just uninstalled the manual one using ./configure and sudo make uninstall

Pidgin works fine now.

Thank You! This fixed the same problem I was having too; Pidgin complaining there was no SSL support. I had a old self-installed version of Pidgin 2.0.1 kicking around in /usr/local. 

Much appreciated!

~ Roobert

---

### Post by upallnight on 2007-10-19
Thanks, worked great:

download pidgin source
extract and cd to pidgin directory
typed ./configure and sudo make uninstall

The ~/.purple/ directory was left intact so all settings were saved.
I prefer using the official ubuntu one anyway!

---

### Post by jocku on 2007-10-23
Worked all right. Thank you. Do not really know why it is done like this, but i am happy i can use pidgin again.

---

### Post by ABX on 2007-10-24
> **upallnight said:**
> Thanks, worked great:

download pidgin source
extract and cd to pidgin directory
typed ./configure and sudo make uninstall

The ~/.purple/ directory was left intact so all settings were saved.
I prefer using the official ubuntu one anyway!

Thanks, this solved my problem.

I was getting the SSL errors when I upgraded to Ubuntu 7.10.

---

