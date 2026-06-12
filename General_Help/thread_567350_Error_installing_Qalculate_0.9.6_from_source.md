---
title: "Error installing Qalculate 0.9.6 from source"
date: 2007-10-04
forum: General Help
---

### Post by BuilderQ on 2007-10-04
Since the latest version of Qalculate is only available as source, I downloaded libqalculate-0.9.6.tar.gz and qalculate-gtk-0.9.6.tar.gz. Then (figuring I should install libqalculate first) I extracted libqalculate, navigated to the appropriate folder, and typed **./configure** (which I planned to follow with** make** and **sudo checkinstall -D**, per the instructions on [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)). This failed, however, and I got this error message: > checking for cln-config... /usr/bin/cln-config
checking for CLN - version >= 1.1.0... no
*** Could not run CLN test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means CLN was incorrectly installed
*** or that you have moved CLN since it was installed. In the latter case, you
*** may want to edit the cln-config script: /usr/bin/cln-config.
configure: error: No suitable installed version of CLN could be found.
Synaptic shows that I have both the libcln4 and libcln-dev packages, which are version 1.1.13-2. How should I handle this?

---

### Post by GreenfieldMark on 2008-01-24
Hey, I'm having the exact same problem. I don't suppose you figured out how to fix it by now because I am fairly stumped.

---

### Post by Fixman on 2008-04-02
Also me!

---

