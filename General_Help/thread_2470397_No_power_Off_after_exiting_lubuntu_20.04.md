---
title: "No power Off after exiting lubuntu 20.04"
date: 2021-12-28
forum: General Help
---

### Post by cpirnie on 2021-12-28
After exiting lubuntu 20.04, screen goes blank, but laptop power remains on indefinately

---

### Post by guiverc on 2021-12-28
You've not provided much to go on.

- I wonder if you're using the GA or HWE kernel (*Ubuntu LTS release users have two kernel stack choices, with Lubuntu the install media decides which stack you're using; if you installed with Lubuntu 20.04 or 20.04.1 media the GA stack is used; if you used 20.04.2 or later the HWE stack is used...   switching the stack can solve these issues thus this thought*).

The command `uname -r` will tell you what kernel is being used; it'll respond with 5.4 if you're using the GA kernel, but 5.11 if using the HWE kernel at 20.04.3  (5.13 when at 20.04.4).  For more details see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

- what else did you try?   If it was me I'd try commands like

```
sudo shutdown -h now
```

```
systemctl poweroff
```

```
poweroff
```

It's possible they'll all respond the same way, but if they don't you've gained more information and a possible workaround may help.

On larger computers turning the power off is very complicated; thus why `shutdown` commands don't by default turn off power (*why you need the -h flag** to halt power too*); which is different to what most users expect having only used small PCs or windows designed to work on small computers (*not mainframes, super computers* etc).  This isn't your issue though, but I suspect it's kernel not dealing well with your hardware, thus why I started with the kernel stack you're using (*GA/HWE as swapping stack very often fixes; using GA if not using a newish device; and using HWE if using a newish device*)

---

### Post by Autodave on 2021-12-28
Also, make sure that you do not have a powered USB hub connected.

---

