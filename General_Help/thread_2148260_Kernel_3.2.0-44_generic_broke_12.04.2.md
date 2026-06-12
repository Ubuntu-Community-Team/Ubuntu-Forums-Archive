---
title: "Kernel 3.2.0-44 generic broke 12.04.2"
date: 2013-05-24
forum: General Help
---

### Post by NM5TF on 2013-05-24
sooooooo......system has been working great running 12.04.2 LTS...:p

this morning update mgr wanted to install 17 updates...new kernel 3.2.0-44
was amongst them....

during install, I noticed a couple of depmod error messages stating that
the new kernel had problems & was not being installed....it was being
rolled back to previous state....OK :frown:

install finished & asked for a reboot which I did.....

GRUB came up with the new kernel at top of list to my surprise...:-k
I selected it to see what would happen.....[-o<

it didn't get very far before up came the all too familiar message stating
"your system is running in low graphics mode"

WTF :confused:

I have an AMD Athlon X 2 @ 2.1 GHz and nVidia graphics card.....

all these issues were resolved many kernels back....what happened:(

---

### Post by grahammechanical on 2013-05-24
May be it was not installed correctly. May be a proprietary driver is not compatible. Who knows? Who can say? I stop trusting Nvidia drivers when I was testing 12.10 ISO images.

Regards.

---

### Post by NM5TF on 2013-05-31
the release of the new kernel 3.2.0-45 has fixed the problem this morning

still can't find how to mark thread as SOLVED....

maybe some MOD/ADMIN can do so....

---

### Post by Karlchen on 2013-05-31
Hello, NM5TF.

> the release of the new kernel 3.2.0-45 has fixed the problem this morning Great. :D 

> still can't find how to mark thread as SOLVED.... Go to [your initial post]("http://ubuntuforums.org/showthread.php?t=2148260&p=12661790#post12661790") and edit it. There must be a way of changing the status flag to [solved].

Karl

---

