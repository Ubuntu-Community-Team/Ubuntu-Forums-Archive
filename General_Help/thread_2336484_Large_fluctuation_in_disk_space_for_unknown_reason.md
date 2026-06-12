---
title: "Large fluctuation in disk space for unknown reason"
date: 2016-09-08
forum: General Help
---

### Post by f1ndingwalden on 2016-09-08
Hello, I am running Ubuntu 15.04, and have been watching large fluctuations in my disk space occur. I witnessed a jump from 64gb free to 41gb free in the course of one hour. I then updated, restarted and logged back in. I ran apt-get clean and autoclean, but it was still at 41gb. I was only running firefox and spotify and a few terminals with vim, but nothing that should be consuming anywhere close to that amount of space. I also saw that tor was running when I executed 'top', so I killed it because I did not ever intentionally run that. Then, as I was sitting here, I watched it jump back up to 91gb!! :confused:

I have no idea what is causing this. I am currently running ```
sudo grep '^\s*[0-9\.]\+G'
``` but as I have a large amount of disk space, it is taking a long time to return.
Any help is appreciated.
Thanks.

---

### Post by QIII on 2016-09-08
Duplicate of [https://ubuntuforums.org/showthread.php?t=2336483](https://ubuntuforums.org/showthread.php?t=2336483).

Closed.

---

