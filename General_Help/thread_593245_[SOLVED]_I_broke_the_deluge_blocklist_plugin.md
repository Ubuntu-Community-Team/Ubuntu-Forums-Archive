---
title: "[SOLVED] I broke the deluge blocklist plugin"
date: 2007-10-27
forum: General Help
---

### Post by colllin on 2007-10-27
Upon trying to setup the blocklist plugin for deluge i entered in the url incorrectly. Now the plugin keeps trying to download from that url and it won't let me click on preferences again to change it.

So is there a way to figure out what file(i'm guessing it's a text file) the url got saved to. And can if i delete the url from the file or the whole file will that fix the problem?

---

### Post by kingcharles1666 on 2007-10-27
try te files in:

~/.config/deluge/

---

### Post by colllin on 2007-10-27
I deleted the blocklist.conf file in that directory and that did the trick.

thanks kingcharles

---

