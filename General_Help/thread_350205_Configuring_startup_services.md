---
title: "Configuring startup services"
date: 2007-01-31
forum: General Help
---

### Post by rohandhruva on 2007-01-31
Hi,

I previously used to use sysv-rc-conf program to configure startup services. However, with the new init system, this seems not to work. I want to disable apache2, hplip etc at startup. I used System -> Admin -> Services, but it does not work - SXXapache2 file is still there in /etc/rc2.d. I know I can delete the respective S and K files and be done with it, but is there a "cleaner" solution ? :D 

Thanks !

---

### Post by Hanzerik on 2007-01-31
I beleave what your looking for is "rcconf"
apt-cache search rcconf

---

### Post by rohandhruva on 2007-01-31
Thank you for the quick reply. I will try it and reply here :)

---

