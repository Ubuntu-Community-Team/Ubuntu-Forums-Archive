---
title: "System Clock out of sync?"
date: 2013-02-10
forum: General Help
---

### Post by MiD-AwE on 2013-02-10
Hi all,

I have not been able to compile the passed two Kernel updates with the NVIDIA CUDA drivers  because of an error that says my system clock is out of sync within the past 24 hours. So I'm stuck with version 35 when I now have 37 as the latest.

I'm sure this is simple to fix but I don't know what to do. 

Please advise. Thank you
 :confused:

---

### Post by Bufeu on 2013-02-10
If you dualboot XP or any other Widnows, try this:
> **QIII said:**
> If you have XP/Ubuntu in a dual boot configuration,  you may be running into the dreaded UTC settings gremlin.

Do

```
sudo cp /etc/default/rcS /etc/default/rcS_backup
``````
sudo  gedit /etc/default/rcS
```Scroll down to the line that says "UTC=yes"  and change it to "UTC=no".

---

### Post by MiD-AwE on 2013-02-10
Yes I dual boot and when I first experienced this issue is after having had used Windows for a couple days due to a productivity app I needed (no option in Ubuntu for AutoCAD).

I followed your instructions and UTC=no is set. Is it likely that I also need to check my BIOS?

I'm going to reboot now and see if it is fixed. Also, I'll check BIOS just in case. :D

---

### Post by Bufeu on 2013-02-10
> **MiD-AwE said:**
> Yes I dual boot and when I first experienced this issue is after having had used Windows for a couple days due to a productivity app I needed (no option in Ubuntu for AutoCAD).

I followed your instructions and UTC=no is set. Is it likely that I also need to check my BIOS?

I'm going to reboot now and see if it is fixed. Also, I'll check BIOS just in case. :DYea, checking the BIOS, just in case, can be a good thing to do.

---

### Post by MiD-AwE on 2013-02-10
:KS

Awesome! Thank you for the quick reply. It worked perfectly no problems!

I would mark this as solved but I can't seem to find the option.

---

### Post by Bufeu on 2013-02-10
> **MiD-AwE said:**
> :KS

Awesome! Thank you for the quick reply. It worked perfectly no problems!

I would mark this as solved but I can't seem to find the option.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

