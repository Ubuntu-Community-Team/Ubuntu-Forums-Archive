---
title: "skittish ubuntu"
date: 2014-12-18
forum: General Help
---

### Post by trav9595 on 2014-12-18
I did a fresh install of ubuntu latest.... it seems to be very skittish but maybe thats my aging laptop....is the new version like this to others????
also what is a terminal script to make my SSD trim every day..?????

---

### Post by QIII on 2014-12-18
Hello!

Which release are you calling the "latest"?  "Skittish" is hard to quantify, so it would be difficult to say if others are seeing the same.

Depending on the manufacturer of the SSD, a cron job may already be set up for you at /etc/cron.weekly/fstrim.

You can move that to cron.daily.  You can also modify it if you like.

---

