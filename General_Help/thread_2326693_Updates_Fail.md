---
title: "Updates Fail"
date: 2016-06-03
forum: General Help
---

### Post by rosswmcgee on 2016-06-03
I have two computers running Ubuntu 1604lts. One of the updaters is yellow in color and it works fine. The other computer the updater is black and I get failed to fetch messages and realize somehow I need to reset the settings but so far editing has not worked. The same DVD installed both ubuntu. When I try to edit the save is grayed out.

---

### Post by wildmanne39 on 2016-06-05
*Thread moved to **General Help**.*

---

### Post by themainliner2 on 2016-06-05
What happens if you issue **sudo apt-get update** at the command line?

---

### Post by X-RED_Tech on 2016-06-05
> **themainliner2 said:**
> What happens if you issue **sudo apt-get update** at the command line?

+1
Post the error messages if any. If no errors then you can proceed to fully update your system:
```
sudo apt upgrade
sudo apt full-upgrade
```

I hope you didn't somehow add your Debian ISO as a software source ;). Otherwise **do not run any of the above**&#8203; before removing such source.

---

