---
title: "Full System Repair"
date: 2008-03-01
forum: General Help
---

### Post by sadeghi on 2008-03-01
Hi
Is there any way to have a full system check for errors or broken package installations and other erros?

---

### Post by y-lee on 2008-03-01
The following will run the system file check program [ fsck ]("http://en.wikipedia.org/wiki/Fsck")on next boot

```
sudo touch /forcefsck
```

This checks for and fixes broken packages:

```
sudo apt-get update
sudo apt-get install --fix-missing
```

For more see[ Cleaning up a Ubuntu GNU/Linux system]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

---

### Post by sadeghi on 2008-03-01
> **y-lee said:**
> The following will run the system file check program [ fsck ]("http://en.wikipedia.org/wiki/Fsck")on next boot

```
sudo touch /forcefsck
```

This checks for and fixes broken packages:

```
sudo apt-get update
sudo apt-get install --fix-missing
```

For more see[ Cleaning up a Ubuntu GNU/Linux system]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

Thanks, I'll post the result later.

---

