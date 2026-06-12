---
title: "dkpg error message, synaptic and update manager will not operate"
date: 2007-11-04
forum: General Help
---

### Post by nickfrazier1 on 2007-11-04
I tried to install Myth TV and I received an error message. After closing the installation and attempting to open synaptic package manager, I received the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I attempted to open a terminal window and enter in the recommended command and it responds with:

dpkg: requested operation requires superuser privilege

Neither the update manager or synaptic package manager will work independently due to this needed correction.

I would still like to install MythTV and correct this problem. However if I need to remove it to do so, I obviously would do so willingly. 

Thank you for your recommendations. I've found the forums priceless and haven't needed to make a post in the 5 months I've used Ubuntu.

---

### Post by taurus on 2007-11-04
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nickfrazier1 on 2007-11-04
I should have known it was a sudo command. 
It worked perfectly. Thank you very much.

---

