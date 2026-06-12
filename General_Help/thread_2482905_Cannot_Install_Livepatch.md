---
title: "Cannot Install Livepatch"
date: 2023-01-13
forum: General Help
---

### Post by testudo2 on 2023-01-13
Running Ubuntu 22.04

After removing Livepatch and aborting an attempt to re-install it, I am receiving the following error when subsequently trying to install:

```
....Notebook-PC:~$ sudo pro enable livepatch
One moment, checking your subscription first
Installing canonical-livepatch snap
Stderr: error: cannot perform the following tasks:
- Run configure hook of "canonical-livepatch" snap if present (run hook "configure": cannot locate base snap core: No such file or directory)

```
I have tried:

```
sudo snap refresh core 

```

and received

```
snap "core" has no updates available
```

Any assistance is appreciated.


<SOLVED> I had broken SNAP cores.  I deleted and reinstalled them, rebooted and was able to install Livepatch.

---

