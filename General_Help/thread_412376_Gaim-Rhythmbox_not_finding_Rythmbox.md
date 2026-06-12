---
title: "Gaim-Rhythmbox not finding Rythmbox"
date: 2007-04-18
forum: General Help
---

### Post by venator260 on 2007-04-18
I've been trying to install Gaim-Rythmbox for quite awhile now, and have been installing dependencies (many), and am now stuck.

When I run ./configure, I get this error

```
checking for rhythmbox... configure: error: Package requirements (rhythmbox >= 0.6) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

I have Rhythmbox 0.9.6 installed, so I'm stuck. I just figured out how to realize what dependencies I need for a certain program to install, so I'm sure the answer is quite simple.

---

### Post by thephotoman on 2007-04-18
Rhythmbox does not have a file for development headers.  Therefore, my best advice would be to run the following commands:

sudo apt-get install apt-src
sudo apt-src install rhythmbox

apt-src iis much like the regular apt-get, but it fetches and compiles the source packages instead of using the precompiled binary files we're used to.

---

### Post by venator260 on 2007-04-19
Ok, I did those two things, same result.

---

### Post by venator260 on 2007-04-20
*bump* Still having this problem after upgrading to Fiesty and consequently Rhythmbox 0.10

---

