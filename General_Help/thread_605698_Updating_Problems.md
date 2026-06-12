---
title: "Updating Problems"
date: 2007-11-07
forum: General Help
---

### Post by EyourTe on 2007-11-07
I tried to update and i accidentally shut down while it still was and now when i try it gives me this message
[B]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor[/B]t.

and i tried to log into my root account but it says my password wasn't correct.

anyone have any suggestions? other then reinstalling.

I have compiz fusion and i did not update to 7.10 yet.

Thank you in advance.

---

### Post by taurus on 2007-11-07
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

