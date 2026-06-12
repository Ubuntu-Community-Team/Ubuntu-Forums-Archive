---
title: "Update to the latest kernel on ubuntu 14.04"
date: 2015-01-18
forum: General Help
---

### Post by soumoks on 2015-01-18
I am currently on a fresh install of ubuntu 14.04.1 64-bit with kernel 3.13.0-44-generic and use this machine for working with openCV only.
However openCV gives me a error when I try accessing the camera after running a program.
```

libv4l2: error turning on stream: Invalid argument
VIDIOC_STREAMON: Invalid argument

```
This apparently happens because of a bug in the linux kernel which doesn't like the program being terminated with ctrl^c. The solution according to a quick search is to update the kernel to the latest.
Can anyone guide me on this? 
Thanks

---

### Post by speartip on 2015-01-18
Before you update to the very latest it might be worth trying the 3.16 kernel that is in the repos.
```
sudo apt-get install linux-generic-lts-utopic
```

---

### Post by soumoks on 2015-01-18
You're a godsend mate! :) Thank you!
Followed your instruction and updated to 3.16 and that problem is gone.

---

