---
title: "Chroot error.."
date: 2006-11-10
forum: General Help
---

### Post by Iarwain ben-adar on 2006-11-10
Hi everybody,

Today i wanted to make a customized live-cd.
Following [this](https://help.ubuntu.com/community/LiveCDCustomization/6%2e06) guide, i have to ```
sudo chroot edit
```..

Problem is this:
```
iarwain@iarwain-desktop:~/music/livecd$ sudo chroot edit
chroot: kan het commando `/bin/bash' niet uitvoeren: Toegang geweigerd
iarwain@iarwain-desktop:~/music/livecd$            
```

Translated it says that i can't execute /bin/bash: access denied :?

How do i go to solve this one?


Iarwain

---

### Post by Iarwain ben-adar on 2006-11-11
Bumper


Iarwain

---

### Post by appa on 2006-11-13
i have the same problem and have been looking on google and the forums for about 2 weeks and found nothing....anyone?

when i run:
```

mule% sudo chroot /mnt/polarbear /bin/bash
chroot: cannot run command `/bin/bash': Permission denied
mule% ls -l /mnt/polarbear/bin/bash
-rwxr-xr-x 1 root root 648400 2006-08-03 09:28 /mnt/polarbear/bin/bash
mule% ls -l /bin/bash
-rwxr-xr-x 1 root root 664084 2006-04-21 16:51 /bin/bash
mule%

```

---

