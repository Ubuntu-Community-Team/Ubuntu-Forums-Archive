---
title: "Error reading lock file /home/bitcoin/.lnd/.lnd.conf.swp: not enough data read"
date: 2019-07-21
forum: General Help
---

### Post by kineticmb on 2019-07-21
Hi all,

I went to edit the lnd.conf but am receiving an error as above. Where as previously it opened the lnd.conf file , it now opens a blank file with .swp tagged to the end of the file.
Any idea how to resolve this and recover the file for editing? The content of the file is still intact but I just cant open it to edit any longer.
Many Thanks,

---

### Post by kineticmb on 2019-07-21
sudo nano /home/bitcoin/.lnd/lnd.conf is the command I use to open the file when the error occurs. I have not had any issue opening this file historically.

The file is not corrupted as when I use the command cat /home/bitcoin/.lnd/lnd.conf it brings up all of the content of the configuration file without issue.

---

### Post by kineticmb on 2019-07-24
Bump

---

