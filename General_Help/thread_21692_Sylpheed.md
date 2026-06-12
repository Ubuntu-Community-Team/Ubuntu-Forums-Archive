---
title: "Sylpheed"
date: 2005-03-23
forum: General Help
---

### Post by plewisfdx on 2005-03-23
I want to install Sylpheed.  It appears to be in the "Universe" repository, so I uncommented them, and "apt-get update".

When I apt-get install sylpheed, this is what I get:

"The following packages have unmet dependencies:
  sylpheed: Depends: libcompfaceg1 but it is not installable
            Depends: libgdk-pixbuf2 (>= 0.22.0-7ubuntu1) but it is not installab le
            Depends: libglib1.2 (>= 1.2.0) but it is not installable
            Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
E: Broken packages"

I thought apt-get was supposed to resolve the dependencies.

Any ideas?

thanks,

phil

---

### Post by plewisfdx on 2005-03-23
I fixed it.

The Synaptics Program Mgr. works better than the command line.  It fixed the things I screwed up on the command line.

---

