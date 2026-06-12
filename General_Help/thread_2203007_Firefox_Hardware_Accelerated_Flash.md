---
title: "Firefox Hardware Accelerated Flash"
date: 2014-02-01
forum: General Help
---

### Post by d4m1r on 2014-02-01
Hey guys, so I am using the latest version of Firefox under Ubuntu 12.04 and a Intel 4000 HD.

Basically, I can enable hardware acceleration just fine and the performance is better BUT it totally screws up the picture....Looks very bright and pixelated. Have tried restarting, etc, nothing fixes it....Except going back to software acceleration. 

[IMG]http://i.imgur.com/pw6jJcD.png[/IMG]



Any idea's? :confused:

---

### Post by mikewhatever on 2014-02-01
Flash on Linux doesn't support hardware accelleration.

---

### Post by mc4man on 2014-02-01
How are you enabling hwacell? Works fine here with Intel 4000 but I've only done so on 13.10 & now 14.04

---

### Post by d4m1r on 2014-02-01
> **mikewhatever said:**
> Flash on Linux doesn't support hardware accelleration.

Yes, actually it does....

> **mc4man said:**
> How are you enabling hwacell? Works fine here with Intel 4000 but I've only done so on 13.10 & now 14.04

/etc/adobe/mms.cfg

EnableLinuxHWVideoDecode=1
OverrideGPUValidation=1

---

### Post by mikewhatever on 2014-02-01
So, you mean it can be enabled, but doesn't work? ...because if it did, you wouldn't be asking how to fix it, right?

I've said "not supported", because no one works towards enabling it by default on Linux.

---

### Post by d4m1r on 2014-02-01
It can be enabled and it does work....Just messes up the picture at the same time as shown in the screenshot.

---

### Post by monkeybrain20122 on 2014-02-01
It does work (on Youtube) and it doesn't mangle the picture like in OP, but embedded videos crashes 100% of the time and there are crashes on non embedded ones as well though it is kind of a hit and miss. Also gpu acceleration doesn't work on all sites, actually only Youtube so far even though it is spectacular when it does work. But I have a Nvidia card, others may have different experience with different hardware.

---

