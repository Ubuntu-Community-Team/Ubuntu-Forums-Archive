---
title: "Unable to install a True Type Font which has a Filename ending in an underscore"
date: 2013-11-04
forum: General Help
---

### Post by desmonddevlin on 2013-11-04
I am trying to install fonts using sudo gnone-font-viewer <filename>.ttf however the True Type files which have a filename ending in an underscore are uninstallable.

How do I get round this? I'm on Ubuntu 13.04.

---

### Post by Dennis N on 2013-11-04
Copy the font file into **/usr/share/fonts** or **~/.fonts** and they should be available to applications.

---

