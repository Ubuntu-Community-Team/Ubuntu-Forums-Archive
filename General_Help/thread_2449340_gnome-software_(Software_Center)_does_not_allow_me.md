---
title: "gnome-software (Software Center) does not allow me to install software"
date: 2020-08-25
forum: General Help
---

### Post by deck on 2020-08-25
Finally got upgraded to 20.04 and am still having issues.  This one is that when I run the Software Center, I am not allowed to install software.  I used to get queried to input my password as a sudoer but now I do not get that query and am told I do not have permission to install software.  I am in the group sudo and can run sudo from a command line.  Clues as to what I am missing?

deck

---

### Post by tea for one on 2020-08-25
I can't offer any exact advice about how to fix the authentication of gnome-software but here are some suggestions to establish the depth of this problem.

Can you use apt OK? i.e. ```
sudo apt install synaptic
```

Having installed synaptic, does it authenticate your user?

If the upgrade has corrupted your user profile, possibly try and create another user with admin privileges?

To be honest, when sudo/admin gives difficulties, I would seriously consider installing a fresh version of 20.04 and adding my back-up.

---

### Post by dinkidonk on 2020-08-25
I cannot see what installing "synaptic" would do, the package manager "Muon" is already installed as an alternative to the software center. Try to run command "groups" in a terminal and see if you are in the "sudo" group, if not that's your problem.

---

### Post by tea for one on 2020-08-25
> **dinkidonk said:**
> I cannot see what installing "synaptic" would do, the package manager "Muon" is already installed as an alternative to the software center. Try to run command "groups" in a terminal and see if you are in the "sudo" group, if not that's your problem.

Installing synaptic would allow the OP to double check admin privileges with package management utilities when gnome-software was misbehaving.

There had been no activity in this thread for 11 hours which often means that these type of problems are very difficult to diagnose and provide workable solutions.

Hence, I was offering **suggestions** rather than solutions.

The OP already mentioned:-

> I am in the group sudo and can run sudo from a command line

---

### Post by deck on 2020-09-09
Finally just fresh installed of  20.04.  I had too much cruft from multiple upgrades over the last decade or so that just had to be blown out to get things working correctly.  I backed up my home directory to a different partition on a different drive and did the fresh install.  I have been bring back in old data directory by directory to get things running.  And the Software Center works great now.

deck

---

