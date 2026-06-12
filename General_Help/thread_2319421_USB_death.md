---
title: "USB death?"
date: 2016-04-04
forum: General Help
---

### Post by ELMIT on 2016-04-04
On my system I have 18 USB-3 hard disk attached. Worked fine over the past years. They are connected via USB-3.0 hubs to the USB port on the computer.

A month ago, one hard drive was not recognized. I thought on a hardware failure.
I swapped harddisks first and then 4 hard disks were not recognized anymore. 
I swapped hubs, but could not figure out any useful information of that.

Above were only USB-3 ports.

Then my printer / scanner stopped to be recognized (USB-2)
Clearly that has nothing anymore with the hard disks or USB hubs to do!

I changed the motherboard.

Still the same.

It must therefore be something on the system. How can I track that down?

uname -a
Linux ronald-desktop 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by sudodus on 2016-04-04
I don't understand what is happening, but I can suggest some actions to explore it.

- Try all current versions (of Ubuntu or your favourite flavour) ***live***,

12.04.1 LTS, 14.04.1 LTS, 14.04.4, 15.10, Xenial Xerus (16.04 LTS).

- Try also Debian Jessie which is using the kernel series 3.16: [Jessie will ship Linux 3.16](https://bits.debian.org/2014/07/kernel-version-for-jessie.html)

---

### Post by stalkingwolf on 2016-04-04
have you run the recovery mode?

---

### Post by pqwoerituytrueiwoq on 2016-04-04
When you say USB hub are you referring to the internal onboard one or to a external one, if it is external i would guess the power adapter on it failed, or the hub failed, possibly taken out by the power brick

---

