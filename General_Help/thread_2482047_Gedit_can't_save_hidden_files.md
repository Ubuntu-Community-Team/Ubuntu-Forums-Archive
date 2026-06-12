---
title: "Gedit can't save hidden files"
date: 2022-12-17
forum: General Help
---

### Post by mathuhenry2 on 2022-12-17
This seems to be a new problem as I can't find anything on Google or in the forums. I have a fresh install of Ubuntu 22.10. The native text editor doesn't have Cobalt theme (just Cobalt light), so I installed Gedit through the Software Center. I can open hidden files, and I an save normal files. But I cannot save hidden files for permission reasons. I've never seen anything like this before. In the Software Center, I gave Gedit every permission possible, and the location I'm saving to is under my permission domain (I can save unhidden there).

---

### Post by howefield on 2022-12-17
Thread moved to the "*General Help*" forum for a better fit.

---

### Post by mIk3_08 on 2022-12-18
> **mathuhenry2 said:**
> But I cannot save hidden files for permission reasons. I've never seen anything like this before.  Have you tried to use nano text editor? Maybe it can help you to save edited hidden files temporarily. Regards and cheers.

---

### Post by Impavidus on 2022-12-18
I'm not familiar with Software Centre. I'm wondering whether you may have installed a snap version of gedit instead of the regular deb version, for which you normally cannot set permissions. Any output from```
snap list gedit
```?
You can install the regular version with```
sudo apt install gedit
```

---

### Post by mIk3_08 on 2022-12-19
> **mathuhenry2 said:**
> This seems to be a new problem as I can't find anything on Google or in the forums. I have a fresh install of Ubuntu 22.10. The native text editor doesn't have Cobalt theme (just Cobalt light), so I installed Gedit through the Software Center. I can open hidden files, and I an save normal files. But I cannot save hidden files for permission reasons. I've never seen anything like this before. In the Software Center, I gave Gedit every permission possible, and the location I'm saving to is under my permission domain (I can save unhidden there).
mathuhenry2, Impavidus just wanted to know the info about your gedit app. 
you can run as well the command below and paste the results here in thread wrap with code. Regards and cheers.
```
snap list
```

---

### Post by mathuhenry2 on 2023-04-12
Thank you. This got it.

---

