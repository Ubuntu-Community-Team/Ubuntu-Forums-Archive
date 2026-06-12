---
title: "After suspend/resume, CPU constantly at max. frequency with low CPU usage"
date: 2019-03-26
forum: General Help
---

### Post by tuxolero on 2019-03-26
Hi,

I have a fresh install of Xubuntu 18.04 LTS on a factory-new laptop (HP Probook). After suspend/resume, the CPU runs constantly at max. frequency, independently of the low CPU usage (currently 2%) and the CPU fan keeps spinning up and down. Very annoying. I'm currently testing it with no desktop applications running, except the browser I'm using for writing this post, of course.

One thing looks suspicious:
In *top*, there is a process I didn't see before the suspend/resume and that looks hardware control related: irq/141-SYNA308

Where should I start troubleshooting ?

Thanx

---

### Post by speartip on 2019-03-26
Quite often these things are graphics card related.
Have you checked in "Additional Drivers" to see if any Proprietary drivers are offered?

---

### Post by tuxolero on 2019-03-27
Whow ... that's rellay strange ... according to the manufacturer's product page, lspci, and lshw, the laptop uses intel UHD graphics.

But in the "Additional Drivers" tab, it offers NVIDIA proprietary drivers and says I'm currently using noveau.

Now, I'm completely confused.

---

### Post by speartip on 2019-03-28
1st step for me would be to install the offered driver & reboot. You can always uninstall it if it makes no difference.
You may well have a Intel/Nvidia dual Graphics card.
try installing inxi.
Then in a terminal run:
```
inxi -F
```
That may give you more info.

---

### Post by tuxolero on 2019-03-28
OK, I've tried it, but the problem is still there.

Indeed, inxi found
> Card-2: NVIDIA GM108M [GeForce MX130]

I've checked the product description again, and I found a hint hidden in the footnotes.

---

### Post by speartip on 2019-03-28
I do not have Dual Graphic Cards so I'm not familiar with their setup. 
But it could be that by default you're only using the onboard graphics.
Maybe somewhere in the bios you need to change it to use the NVIDIA card.

---

### Post by tuxolero on 2019-04-04
I've found out how to disable the NVIDIA graphics chip, but still no change.

As you wrote ... "often" graphics related. Maybe, this time it's not. Any idea how I can find out whet the irq/141-SYNA308 process is about ?

---

### Post by tuxolero on 2019-05-06
It has turned out that the Synaptics Touchpad is the troublemaker. Normally, I have a keyboard and a mouse attached to the laptop, so I rarely use the touchpad, but yesterday had to used it. And I could see that before the suspend/wakeup the touchpad works normally but afterwards, it is completely unusable. It stutters, just dragging the pointer triggers some clicks on the way (as if I tapped, but i didn't), tapping sometimes works, sometimes not, etc ...

It's not me ... I've been using touchpads on other laptops too and never had problems. And the problems clearly appear after suspend/wakeup and disappear after reboot.

---

### Post by c-launchpadmail on 2019-09-26
Many have been having the same problem and in many cases it is found to be the i2c drivers. 

See if the following command fixes the CPU frequencies going to max 
$sudo modprobe -r i2c_hid && sudo modprobe i2c_hid

If so, then you are affected by this bug: [https://bugzilla.kernel.org/show_bug.cgi?id=204367](https://bugzilla.kernel.org/show_bug.cgi?id=204367)

---

