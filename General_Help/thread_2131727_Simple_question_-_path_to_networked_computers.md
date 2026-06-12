---
title: "Simple question - path to networked computers"
date: 2013-04-02
forum: General Help
---

### Post by fizikz on 2013-04-02
When browsing through the filesystem directories, where can I find mounted the shared directories on the network? Eg. A Windows computer on the home network has a shared folder "Documents" and I want to navigate to it from my Ubuntu machine. I can click Places -> Network, etc, but how can I do this on the command line or through the "Browse for folder/file" button in various applications?

---

### Post by Morbius1 on 2013-04-02
Depends on the version of Ubuntu you are using.

12.04 and earlier: /home/$USER/.gvfs

12.10 and beyond: /run/user/$USER/gvfs

Where $USER is your user name.

---

### Post by fizikz on 2013-04-02
Perfect. Thanks!

---

