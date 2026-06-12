---
title: "Computer Won’t Wake Up From Sleep. Hey everybody."
date: 2020-02-03
forum: General Help
---

### Post by giedosst on 2020-02-03
Hey everybody.


Got a Dell Inspiron 3650 with a Nvida GP107 (GeForce 1050) card on 19.10.


It won’t wake up after I put it to sleep just a blank screen. I’ve tried all nvida proprietary driver options and my computer runs slowly on them and still won’t wake up. The only driver that works is the nouveau but again it won’t wake up.


I’ve tried a bunch of fixes to include the “quiet slash screen nouveau.modset=0” and it still does work.


Past versions of ubuntu with this computer never had this issue.


Does anybody have an suggestions I’m stumped.


Thanks.


Here is some info of my system:

[https://paste.ubuntu.com/p/JMcpMxpsb3/](https://paste.ubuntu.com/p/JMcpMxpsb3/)

---

### Post by CelticWarrior on 2020-02-03
Trying multiples drivers usually results in a mess hard to untangle.
The likely problem is that you didn't **disable Secure Boot** and because of that the drivers weren't loaded, even if correctly installed.

---

### Post by giedosst on 2020-02-03
> **CelticWarrior said:**
> Trying multiples drivers usually results in a mess hard to untangle.
The likely problem is that you didn't **disable Secure Boot** and because of that the drivers weren't loaded, even if correctly installed.

Ok, that's good to know so, I should be able to disable Secure Boot from the BIOS then yes?

---

### Post by CelticWarrior on 2020-02-03
From the UEFI yes. BIOS is old technology that has been replaced by UEFI a long time ago.

---

### Post by giedosst on 2020-02-03
> **CelticWarrior said:**
> From the UEFI yes. BIOS is old technology that has been replaced by UEFI a long time ago.


Thanks!

---

### Post by giedosst on 2020-02-03
Ok, took a look into my UEFI and "secure boot" is disabled.

---

### Post by CelticWarrior on 2020-02-03
Good.

So, the driver you want is 440. And, of course, remove any additional boot parameters that you added meanwhile.

---

### Post by giedosst on 2020-02-03
Hmmm, 

Is that the Nvida proprietary driver because I can only select 435, 390 or 430 from "Additional Drivers".

I take it I'll have to manually install the 440?

---

### Post by giedosst on 2020-02-03
Ok, installing that driver, I hope it works!

---

### Post by CelticWarrior on 2020-02-03
All are proprietary. 440 is the current Nvidia recommendation.
You can try with the just slightly older 435 or add the [graphics drivers PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") that already includes the 440 branch.

---

### Post by giedosst on 2020-02-03
Ok, I installed it and no dice.

The system runs very slowly and it still won't wake up from sleep.

Shaka, when the walls fell...

---

### Post by CelticWarrior on 2020-02-03
Have you purged the previous mess of drivers you installed before? That can and almost always is a problem.

If you did and secure boot is disabled and there are no weird boot parameters... It simply CANNOT be slower than without the drivers, that's just a fact.

---

### Post by giedosst on 2020-02-04
Ok,

I fixed it.

Spent all day removing drivers, installing drivers, changing kernels, nothing, it was a waste of time. Got to the point where even the Nouveav was seizing up. Nothing worked.
 
I backed everything up and rolled back to 18.04 LTS and everything is work fine.

Thanks anyway.

I need to just stay away from the bleeding edge.

---

