---
title: "Unable to perform package upgrades in LXLE 16.04"
date: 2018-05-30
forum: General Help
---

### Post by alynur2 on 2018-05-30
Hi guys, when I perform an update, the updater for Eclectica always shows that when upgrades are avail. the updater is unable to proceed. If I run sudo apt upgrade in a terminal, I get this:

```
96 packages can beupgraded. Run 'apt list --upgradable' to see them.
albert@albert-desktop:~$sudo apt upgrade
E: Could not getlock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lockthe administration directory (/var/lib/dpkg/), is another processusing it?
```

This is upon bootup and the first thing attempted, so I haven't opened anything at this time. How do I solve this problem. I ran into a similar problem in a different distro, don't remember which one it was but I solved it by going into Software and Updates and changing a setting in there, but I can't find anything similar in Eclectica. I can't find any update settings at all. Any ideas?

---

### Post by Frogs Hair on 2018-05-30
Try the following terminal commands one at a time .

```
sudo fuser -vki /var/lib/dpkg/lock; sudo dpkg --configure -a
``` ```
sudo apt update && sudo apt upgrade 
```

---

### Post by alynur2 on 2018-06-10
Thanks Frogs Hair, I think this is what was needed. After running these commands, I ran the updater again and it ran the checks for upgrades and removables with nothing there to be done.

---

