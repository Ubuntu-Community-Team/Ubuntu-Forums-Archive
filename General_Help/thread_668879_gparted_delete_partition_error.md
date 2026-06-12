---
title: "gparted delete partition error"
date: 2008-01-15
forum: General Help
---

### Post by dydo on 2008-01-15
I installed ubuntu on my computer on another partition. I have 2 partitions that are not used and not formatted and when I boot into the ubuntu live-cd and try to delete one of them ( /dev/sda5 and /dev/sda6 ) it comes up with an error saying
```

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5.

```
The number is changed to 6 when I try to delete /dev/sda6. They have a lba flag and thats all. Help is appreciated.

---

### Post by chewearn on 2008-01-16
> **dydo said:**
> I installed ubuntu on my computer on another partition. I have 2 partitions that are not used and not formatted and when I boot into the ubuntu live-cd and try to delete one of them ( /dev/sda5 and /dev/sda6 ) it comes up with an error saying
```

Unable to delete /dev/sda5!
Please unmount any logical partitions having a number higher than 5.

```The number is changed to 6 when I try to delete /dev/sda6. They have a lba flag and thats all. Help is appreciated.

Whichever works:
Right-click on the partition, select unmount.
Right click and select swap off.

---

