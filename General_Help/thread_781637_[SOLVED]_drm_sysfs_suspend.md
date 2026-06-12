---
title: "[SOLVED] drm_sysfs_suspend"
date: 2008-05-04
forum: General Help
---

### Post by Nintendo01 on 2008-05-04
Whenever my Hardy laptop wakes up from sleep it beeps a few times and gives me the message "drm_sysfs_suspend" at the upper left corner of a black screen. Before this message is a series of numbers that seems random every time it wakes up. Here's an example of what it does:

```
I open the laptop lid, it makes a few loud beeps, then displays this:

(9795.534485) drm_sysfs_suspend

30 seconds later, everything is normal
```

The numbers at the beginning seem random each time the computer wakes up, but the drm_sysfs_suspend message is the same each time. After about 30 seconds to a minute, the message goes away and the the password screen is displayed like normal, and everything seems fine. It just gets annoying having my computer beep at me and having to wait over 30 seconds just for it to wake up.

Can anyone help me make this stop?

---

### Post by Nintendo01 on 2008-05-06
Anyone?

---

### Post by jyanek on 2008-05-07
I have the same issue.  Today, I woke the computer up from a suspend.  It beeped maybe 5 times, then came up with the same drm_sysfs_suspend message ... any help would be appreciated

Dell inspiron 1525 with Hardy 8.04

---

### Post by tamias on 2008-05-27
According to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/234239) this is not an error, but it is some debug info which should not be printed. The next kernel upgrade should hopefully include a patch to stop the drm_sysfs_suspend message from occurring.

---

### Post by Nintendo01 on 2008-05-27
YAY!! Someone found what I couldn't! I didn't think it was an error since it didn't do anything besides display that message, but as this confirms that this is just spam (Stupid Pointless Annoying Message) from the Hardy programmers and will be fixed, thanks!

---

