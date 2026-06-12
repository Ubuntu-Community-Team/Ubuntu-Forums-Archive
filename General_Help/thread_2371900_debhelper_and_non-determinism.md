---
title: "debhelper and non-determinism?  ???"
date: 2017-09-19
forum: General Help
---

### Post by yonnie on 2017-09-19
Tried to install the network Epson printer and the Epson ESC/p-r driver balked midway.  Now I get an error about debhelper and strip non-determinism.  I tried to run dpkg but it's still not fixed.  I cannot install the printer, period.  
When I startup Synaptic I get an error msg about a download from ebz.epson. long file name complaining about a signature key.  Is this something to ignore?  Anyhow, I can't get the printer working, this is critical

---

### Post by yonnie on 2017-09-19
This is what Synaptic posts in a box:
E: dh-strip-nondeterminism: dependency problems - leaving unconfigured
E: debhelper: package debhelper is not ready for configuration  cannot configure (current status 'half-installed')

Anybody know what to do?

---

### Post by yonnie on 2017-09-20
FYI---  Anyone know how to resolve this?

---

### Post by oldos2er on 2017-09-20
Moved to General Help for more visibility.

---

### Post by yonnie on 2017-09-23
nobody knows of a solution?

---

### Post by dragonfly41 on 2017-09-23
Perhaps try to install with GDebi Package Installer and check dependencies.
Another useful tool is Y PPA Manager (for PPA installs).

---

### Post by yonnie on 2017-09-23
would that be called gdebi-core?  Iget this after installing gdebi-core.  I thinks it's the same message from Synaptic: W: [http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:](http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:) Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)

---

### Post by yonnie on 2017-09-23
After reboot and running recovery mode I get a message about Package debhelper is not installed.  What is package debhelper?

While running clean I get a message about failure resolving ca.archive.ubuntu.com

---

### Post by yonnie on 2017-09-23
Problem seems to be resolved.  Changed repos and re-installed debhelper and the epson stuff.

thanks for the help!

---

