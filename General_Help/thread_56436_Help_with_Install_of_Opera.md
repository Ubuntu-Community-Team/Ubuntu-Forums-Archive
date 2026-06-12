---
title: "Help with Install of Opera"
date: 2005-08-12
forum: General Help
---

### Post by MasterC on 2005-08-12
I just got Opera from their website, and I can't figure out how to install it. When I open the file, I have three choices: two folders (control.tar.gz and data.tar.gz) and one that says debian-binary. The first two are tar archives and the last is an unknown. Any help would be greatly appreciated! Thanks!

---

### Post by mcmuffy on 2005-08-12
You need to get the .deb file (I can't remember the exact filename).
To install it open a terminal and enter :

sudo dpkg -i filename.deb
where filename is the name of the opera file you downloaded.

---

### Post by yoshic on 2005-08-12
hi, first you should download the debian package suplied by opera, there's one for ubuntu,( in the combo box of distro select ubuntu)  once you 've downloaded, in a root terminal put this:
```
dpkg -i operaxxxxxx.deb
``` 

where "operaxxxxxx.deb" is the name of the file you downloaded... i hope this will be useful :wink:

---

### Post by MasterC on 2005-08-12
I tried the first one, but I get a message that says "Errors were encountered while processing."

The second one says that I need superuser privelages to complete the operation.

---

### Post by wvslkr on 2005-08-12
Try
```
sudo dpkg -i operaxxxxx.deb
```

---

