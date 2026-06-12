---
title: "upgrade didn't work?"
date: 2006-12-20
forum: General Help
---

### Post by thekid on 2006-12-20
Hi

I installed Ubuntu 6.06 LTS a while ago. Then I downloaded Ubuntu 6.10. I put it in my cdrom, ubuntu says i can upgrade the packaegs. So I decided to upgrade my packages. 

But after the upgrade, my firefox is still 1.5, and when I start firefox, I still see Ubuntu 6.06 LTS!

What's going on? did the upgrade not succeed? Please advise. Thanks!
btw, how do I check if I have edgy or not? (the default firefox home page says i am using 6.06 still).


_jay

---

### Post by Azakus on 2006-12-20
Try this code
```
gksudo "update-manager -c -d"
```
That will popup with the newest version of Ubuntu and autoupgrade your packages.
Choose only 6.10. If you see 7.04 don't touch it (still VERY beta).

---

