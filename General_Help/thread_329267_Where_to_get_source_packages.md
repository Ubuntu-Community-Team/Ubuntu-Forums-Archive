---
title: "Where to get source packages?"
date: 2007-01-01
forum: General Help
---

### Post by MWP on 2007-01-01
Hi all,

Where can i get the source packages for tha standard Ubuntu edgy packages?
I see some items have source packages available, but not all?

For example, i would like to get the X and Xgl packages so i can recompile them for machine specific gcc opts.

Is there a repository (or a few) i need to add to get access to them?

Thanks!

---

### Post by smoker on 2007-01-01
click the link below, and scroll down to end of page:

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by Ramses de Norre on 2007-01-01
The repos should be already there, it are the deb-src lines in /etc/apt/sources.list.
To use them: ```
apt-get source package_name
``` this will download the source package to a directory in home.

---

