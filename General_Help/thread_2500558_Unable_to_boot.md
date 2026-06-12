---
title: "Unable to boot"
date: 2024-09-05
forum: General Help
---

### Post by vladimir1128 on 2024-09-05
Hi everyone. I was working on a C++ project and made some serious mistake while trying to iterate the folder, so the OS froze and I had to turn off the laptop. But when I turned it on, it appeared that Ubuntu doesn't start. Actually, after I select the OS in the list, it just shows sort of a grey screen instead of loading. Are there any suggestions on how to fix it or at least how to turn on a text boot mode in order to understand the error? I realize that there might be dozens of the same questions here on the forum, but since it doesn't look like an expected behaviour of a stable OS, I guess it's useful to talk about it as much as possible and attract attention to this issue until it is fixed by the developers :)

---

### Post by tea for one on 2024-09-05
If you power off the PC while the file systems are still mounted, you run the risk of file system damage.
Boot into a "Try Ubuntu" live session
Open a terminal
Identify your partitions
```
sudo parted -l
```
Run fsck on all partitions (brief example below)
```
sudo fsck /dev/sda1
sudo fsck /dev/nvme0n1p1
```

---

### Post by vladimir1128 on 2024-09-05
Thank you for the reply. It found and fixed a lot of errors, but now there's no option to select OS and Windows boots right away :) So I first need to somehow fix the Grub in order to check the result

---

### Post by tea for one on 2024-09-05
Does Windows have priority in your PC (UEFI) boot menu?

---

### Post by vladimir1128 on 2024-09-05
Yes, for some reason it had a higher priority. Thank you for your answers, now it works. Although I insist that it is a bug and Linux should be more stable than Windows in this situation according to its reputation :) But it's not for this topic. I'm new on this forum, so a few additional questions not related to the main question.
1) I am working on a custom game engine on a quite low level, using different XWindow stuff for creating window and handling input. Looks like it's not the easiest thing to work with. Are there specialists in this topic on this forum or should I look for a special C++ programmers forum?
2) Just curious about /dev/sdaN, where N is a number. Is it possible to change a number and not break the OS? :)

---

### Post by tea for one on 2024-09-05
> **vladimir1128 said:**
> Yes, for some reason it had a higher priority. Thank you for your answers, now it works. 
Good news 
Please mark thread as solved - it's very useful for other users/searchers - already done, thank you
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
> Although I insist that it is a bug and Linux should be more stable than Windows in this situation according to its reputation 
Please start a new thread with a complete description of this "bug"
Alternatively, report the bug against a package on [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
> I am working on a custom game engine on a quite low level, using different XWindow stuff for creating window and handling input. Looks like it's not the easiest thing to work with. Are there specialists in this topic on this forum or should I look for a special C++ programmers forum?
[https://ubuntuforums.org/forumdisplay.php?f=310](https://ubuntuforums.org/forumdisplay.php?f=310) or [https://ubuntuforums.org/forumdisplay.php?f=93](https://ubuntuforums.org/forumdisplay.php?f=93)
> Just curious about /dev/sdaN, where N is a number. Is it possible to change a number and not break the OS? 
Start a new thread with full details about why there is a need to activate a change of disk identity

---

