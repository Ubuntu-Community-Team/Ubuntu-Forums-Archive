---
title: "Firefox Beta"
date: 2005-10-13
forum: General Help
---

### Post by fiby on 2005-10-13
Firefox worked gloriously on 5.04,  I just installed 5.10 and know I can't install Firefox beta.  If I use the installer file I get this error when running the ./firefox-installer command: [B] ./firefox-installer-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/B] 
I tried the other file that lets you run from the folder downloaded, not the installer, but when i click the firefox script icon with the little SH it just opens up in a text editor?  

Any ideas?

---

### Post by bsdpro on 2005-10-13
Try this:

ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5

---

### Post by lfittl on 2005-10-13
Install the 'libstdc++5' package ;)

---

### Post by karuptdata on 2005-10-13
Search for the pack in synaptic...i had problems finding it with just apt-get...

---

### Post by z_pod on 2005-10-14
Install missing package (synaptic->search->libstdc)

---

### Post by fiby on 2005-10-14
Thanks for the help. Installing the package worked! Thanks

---

