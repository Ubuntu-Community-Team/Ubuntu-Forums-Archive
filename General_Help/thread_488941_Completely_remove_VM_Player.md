---
title: "Completely remove VM Player"
date: 2007-06-30
forum: General Help
---

### Post by PaulFXH on 2007-06-30
I had installed VM Player (from Synaptic) and want to move back to VMware Server.
Synaptic informed me that it needed to remove VM Player before it installed Server.
It certainly did some removal, but apparently not enough as before Server could be fully installed, a message appeared saying that I must COMPLETELY remove VM Player before Server can be installed.
Can somebody please indicate to me how I may achieve this complete removal?
Thanks
Paul

---

### Post by satx on 2007-06-30
In Synaptic make sure you mark the entry Mark for Complete Removal. You do this by right clicking on the green software check block. See attachment:

SATX

---

### Post by satx on 2007-06-30
Paul:

Easier way maybe:

From terminal: sudo aptitude purge vmware-player

SATX

---

### Post by PaulFXH on 2007-07-01
Yes, thank you.
Your last command line did the trick very nicely for me.
Best wishes
Paul

---

