---
title: "Help skype2 won't install!"
date: 2007-11-21
forum: General Help
---

### Post by shane2peru on 2007-11-21
:cry:Help my Skype 2 beta won't install!  I have downloaded it twice now, and nothing.  I'm running Gutsy Up to date on a 32 bit system.  I have Skype 1.4 installed and works fine.  Here is the terminal output:```

sudo dpkg -i skype-debian_2.0.0.13-1_i386.deb
(Reading database ... 193547 files and directories currently installed.)
Preparing to replace skype 1.4.0.118dynamic+static-0medibuntu3 (using skype-debian_2.0.0.13-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: error processing skype-debian_2.0.0.13-1_i386.deb (--install):
 trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 skype-debian_2.0.0.13-1_i386.deb

```  If you know anything about getting this setup correctly I would greatly appreciate the help! :cry:

Shane

---

### Post by prince_niceguy on 2007-11-21
first of all remove skype using synaptic select skype and right click and select remove completely. this should remove all config files.

now, install your new skype. this should work.

---

### Post by shane2peru on 2007-11-21
Thanks prince_niceguy  your a nice guy!  That worked like a charm.  :oops:  I should have thought of that myself.  Sometimes that 'Windows' mode slips in every now and then and I forget to think.  :)  Thanks.

Shane

---

