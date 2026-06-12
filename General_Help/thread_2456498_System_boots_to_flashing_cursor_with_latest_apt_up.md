---
title: "System boots to flashing cursor with latest apt update"
date: 2021-01-12
forum: General Help
---

### Post by BigErn on 2021-01-12
So I just did my biweekly apt dist-upgrade on my two Ubuntu 20.04 systems, and now neither can boot, but stop at a black screen with a flashing cursor. (this occurs well after the grub menu) . I could kick myself for unwisely doing them simultaneously.

These are older Athlon 64 based machines, each running a geforce card.

If I boot into recovery mode, and then from the recovery menu choose 'resume normal boot', it does manage to load the desktop, but with slow choppy graphics.

Does anyone know what the problem is? 

If not, how can I revert my apt dist-upgrade?

Many thanks.

Update: Choosing from the grub menu kernel 5.4.0 seems to make everything work OK again. I guess the 5.8.0 kernel hosed my system.
Update 2: I suspect that the current nvidia drivers I'm using simply haven't been updated to the 5.8 kernel, which is preventing the desktop environment from starting. I guess I will just wait for a driver update.

---

### Post by ajgreeny on 2021-01-12
The new 5.8.0-36 kernel seems to have caused many problems for users so I imagine a further upgrade will appear fairly soon.

In the previous LTS versions the kernel series upgrades, as in yours from 5.4 to 5.8, did not happen until the point 2 release, ie 20.04.2.
For some reason it has come to 20.04.1 earlier than usual, so you may have to stick with the 5.4 kernel for a while until you see a newer version of 5.8 appear when you boot to it and try it out again.

---

### Post by GhX6GZMB on 2021-01-12
Why is it so incredibly important to upgrade to the latest, bleeding-adge kernel?

Just wait until it's stable.

20.04 LTS works wonderfully. Seems to be pure upgradeitis to me.

---

### Post by BigErn on 2021-01-12
Thanks fellas.

---

### Post by jeremy31 on 2021-01-12
You can use the grub menu/advanced options to boot into a 5.4 kernel where everything should work from there you should be able to 
```
sudo apt remove linux-image-5.8.0-36-generic linux-generic-hwe-20.04 && sudo apt install linux-generic
```
Hopefully that will keep you on the 5.4 LTS kernel

---

### Post by ajgreeny on 2021-01-13
> **ml9104 said:**
> Why is it so incredibly important to upgrade to the latest, bleeding-adge kernel?

Just wait until it's stable.

20.04 LTS works wonderfully. Seems to be pure upgradeitis to me.
The problem seems to be that 20.04.1 installations are now automatically moving to the hwe kernels so users who are unaware of this are sometimes being faced with these difficulties when the 5.8.kernel is added and then boots by default.

I have yet to find why this is happening with the point 1 release; it usually starts only at the point 2 release.

---

### Post by BigErn on 2021-01-14
> **jeremy31 said:**
> You can use the grub menu/advanced options to boot into a 5.4 kernel where everything should work from there you should be able to 
```
sudo apt remove linux-image-5.8.0-36-generic linux-generic-hwe-20.04 && sudo apt install linux-generic
```
Hopefully that will keep you on the 5.4 LTS kernel

This command worked a treat, many thanks.

(Also needed a sudo apt autoremove before the 5.8 kernel was removed from grub.)

---

### Post by GhX6GZMB on 2021-01-14
> **ajgreeny said:**
> The problem seems to be that 20.04.1 installations are now automatically moving to the hwe kernels so users who are unaware of this are sometimes being faced with these difficulties when the 5.8.kernel is added and then boots by default.

I have yet to find why this is happening with the point 1 release; it usually starts only at the point 2 release.

No. I've just done an update, which resulted in 5.4.0-62 being installed. Solid and stable.
The problem is that some users have opted for "Pre-released updates" and perhaps even "Unsupported updates" in their update manager.

'Upgradeitis' brings pain.

---

### Post by kansasnoob on 2021-01-15
> **ml9104 said:**
> No. I've just done an update, which resulted in 5.4.0-62 being installed. Solid and stable.
The problem is that some users have opted for "Pre-released updates" and perhaps even "Unsupported updates" in their update manager.

'Upgradeitis' brings pain.

No, it's not. The Ubuntu images have the HWE version of linux-generic installed by default. It only became apparent when the 5.8 series kernel rolled out. The other flavors are not effected:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1911614)

If that bug report gets no "effects me too" love it will likely never get fixed.

---

