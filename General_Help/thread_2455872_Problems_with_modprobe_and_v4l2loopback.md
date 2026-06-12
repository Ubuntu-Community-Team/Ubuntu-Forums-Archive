---
title: "Problems with modprobe and v4l2loopback"
date: 2020-12-29
forum: General Help
---

### Post by dorpapst on 2020-12-29
I am trying to get v4l2loopback to work and it simply doesn't let me start it. ([https://github.com/umlaeute/v4l2loopback](https://github.com/umlaeute/v4l2loopback))
I installed it following the manual from the link above and I try to start it with:
```
sudo modprobe v4l2loopback
```
Unfortunately I get the following message, also after a reinstall:
> modprobe: ERROR: could not insert 'v4l2loopback': Invalid argument

I tried the following command to have a look which modules I could load:
```
basename -s ".ko" $(find /lib/modules/$(uname -r) -type f -name "*.ko")
```
It includes v4l2loopback which makes me feeling that everything is properly installed.

Does anybody know what is wrong with it?

Kind regards
Lukas

PS: I have seen a lot of similar questions on stack overflow but literally none of them was really helpful. :(

---

### Post by dorpapst on 2020-12-29
I found out one more thing:
> 5.4.0-26-generic  5.4.0-47-generic  5.4.0-51-generic  5.4.0-53-generic  5.4.0-56-generic
5.4.0-45-generic  5.4.0-48-generic  5.4.0-52-generic  5.4.0-54-generic  5.4.0-58-generic
I have several kernels installed and only 56 and 58 have a folder extras/v4l2loopback.ko,
but **uname -r **shows kernel version 5.4.0-58-generic, so I don't think that this could be the problem.

---

### Post by #&amp;thj^% on 2020-12-29
Your sooo close. [https://askubuntu.com/questions/1245212/how-do-i-automatically-run-modprobe-v4l2loopback-on-boot](https://askubuntu.com/questions/1245212/how-do-i-automatically-run-modprobe-v4l2loopback-on-boot)

---

### Post by dorpapst on 2020-12-30
You are right! That actually helped me.
Thank you very much for your answer.

---

### Post by #&amp;thj^% on 2020-12-30
Your Very Welcome...

---

