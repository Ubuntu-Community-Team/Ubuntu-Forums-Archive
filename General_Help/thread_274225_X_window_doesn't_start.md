---
title: "X window doesn't start"
date: 2006-10-09
forum: General Help
---

### Post by mauserrifle on 2006-10-09
After alot of messing around to get XGL to work (which I didn't get to work :( ) X-server window manager won't start automaticly anymore when loggin in. Also partitions that are in Disk manager don't show anymore in 'Computer'
Could this gdm and xorg.conf mess up so much? :-? 
i restored gdm + xorg.conf with backups.

Some advice and help on this would be great. Seems stuff got bit messed up.

Maurice

---

### Post by taurus on 2006-10-09
You might need to reconfigure your X again so from a terminal, do

```

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

---

