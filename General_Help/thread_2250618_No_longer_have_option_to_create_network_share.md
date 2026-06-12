---
title: "No longer have option to create network share"
date: 2014-10-29
forum: General Help
---

### Post by Gottier on 2014-10-29
Ubuntu 14.04

I was checking out network sharing between two of my ubuntu computers, but when ubuntu tries to install samba for sharing, I didn't notice that it wanted to install something until after I had already closed the installation.

So I thought I would reinstall samba.

```

sudo apt-get autoremove samba samba-common
sudo apt-get autoremove system-config-samba
sudo apt-get install samba samba-common
sudo apt-get install system-config-samba cifs-utils

```

But now I no longer have the context option to create a network share, and the network sharing tab is gone when I right click on a directory in nautilus. How can I fix?

---

### Post by Gottier on 2014-10-29
I figured it out.

sudo apt-get install nautilus-share

then had to restart

---

### Post by Gottier on 2014-10-29
I figured it out.

sudo apt-get install nautilus-share

then had to restart

---

