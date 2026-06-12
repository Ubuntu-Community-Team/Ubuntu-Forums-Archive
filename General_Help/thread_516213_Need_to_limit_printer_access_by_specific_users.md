---
title: "Need to limit printer access by specific users"
date: 2007-08-02
forum: General Help
---

### Post by nwh2 on 2007-08-02
On a stand-alone machine running Fiesty, I have accounts for various users. I want to limit printing to some users and not allow others to print (local printer). How can I do this? Using groups, somehow? Thanx

---

### Post by TBerben on 2007-08-04
CUPS has an 'allowed' users as well as a 'blocked' user list. You can create a group 'printing' or something similar, put that group in the 'allowed' list. Any users not belonging to that group should be blocked after that.

---

