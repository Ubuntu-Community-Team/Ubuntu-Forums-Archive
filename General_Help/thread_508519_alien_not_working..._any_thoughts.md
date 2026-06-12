---
title: "alien not working... any thoughts?"
date: 2007-07-24
forum: General Help
---

### Post by Krusz on 2007-07-24
Here's what happens:

sudo alien flash-plugin-9.0.48.0-release.i386.rpm
sh: rpm: not found
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} flash-plugin-9.0.48.0-release.i386.rpm":  at /usr/local/share/perl/5.8.8/Alien/Package.pm line 482.

any thoughts?

---

### Post by AceofSpades19 on 2007-07-24
you can just install flash from synaptic

---

### Post by Majorix on 2007-07-24
You don't have the rpm package installed it seems.

---

### Post by bodhi.zazen on 2007-07-24
You should use ALIEN as a last resort ...

1. Always go with the Ubuntu repositories first 

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

2. If that fails, you can try an Ubuntu .deb or build form source.

---

