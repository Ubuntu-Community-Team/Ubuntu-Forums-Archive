---
title: "Hard Drive Partitions"
date: 2008-02-28
forum: General Help
---

### Post by Maxcore on 2008-02-28
Hello everyone. This is my second time installing Ubuntu on my computer, the first time was just for testing out and now that MS has discovered a way to detect cracked Vista copies I was forced to find a free alternative. The first time I used Ubuntu I noticed that it mounted my hard drive partitions on the desktop so I could view them. Now that I am running it again they aren't there. Has a setting changed or something or are all these files not accessible from Ubuntu. This is really important because my Vista copy has locked me out and like my entire life was on there. It would be really great if someone could help me out.

---

### Post by taurus on 2008-02-28
Maybe because the last time you used Vista, you didn't shut it down cleanly.  Therefore, it won't be mounted automatically from /etc/fstab without the force option.

Open a terminal and post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

