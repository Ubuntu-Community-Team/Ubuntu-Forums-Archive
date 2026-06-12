---
title: "ulogd errors"
date: 2006-11-17
forum: General Help
---

### Post by wacole on 2006-11-17
Just upgraded Hoary to Dapper using the online upgrade process.  Got an error message from the upgrade process for ulogd and ulogd-pcap: "subprocess /usr/bin/dpkg returned an error code (1)".

Tried reinstall on both.  Error message "ulogd: subprocess post-installation script retruned error exit status 126.  ulogd-pcap: dependency problems - leaving unconfigured."

Then tried a total removal (w/a plan to install fresh) on both.  Ulogd-pcap removed completely. Ulogd returned "ulogd: subprocess pre-removal script returned error exit status 126"

I'm stuck.  Help please.

Thanks very much,

---

### Post by wacole on 2006-12-22
Found the problem; the /etc/init.d/ulogd file was corrupted.   I had a backup image so I copied the ulogd file from the image to the active drive and all was well (had to do this w/sudo).

---

