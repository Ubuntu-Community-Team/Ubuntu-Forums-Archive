---
title: "apt or dpkg lock file"
date: 2007-11-03
forum: General Help
---

### Post by maestrobwh1 on 2007-11-03
I keep getting this on ONE of my machine and it happens even when no package manager has been running:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

sometimes it is on /var/lib/dpkg/lock as well.

I generally do a 
sudo rm [path] to allow me to do my work.  

Is there a way to keep this from happening?  I opened software sources and it isn't set to fetch updates automatically.

---

