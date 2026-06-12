---
title: "Risk of Replacing Linux Headers?"
date: 2014-04-22
forum: General Help
---

### Post by regnumimbriumx on 2014-04-22
Hello All,


First off, of course, thanks for the great work that you're all doing! The world is a safer place, thanks to your efforts.


I'm aware that there is no perfect security to be had and that security culture is a way of living; I just want to decrease the odds that my data can be accessed as much as possible and avoid introducing new holes.


To that end, I'm wondering about the risk of replacing my linux headers on my laptop. I'm currently using 14.04 (although I'm not opposed to downgrading), but some of my hardware drivers don't work out of the box. To get them working, it has been suggested that these steps be followed:


1) Add the following to /etc/modules:
```
loop
lp
chromeos-laptop
cyapa
rtc
i2c-i801
i2c-dev

```

2) Download new headers:
```
wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-saucy/linux-headers-3.11.0-031100-generic_3.11.0-031100.201309021735_amd64.deb

```

3) Install new headers:
```
sudo dpkg -i linux-headers* linux-image*



```This does make my system usable, but I'm concerned about any security vulnerabilities that may open up. Do I need to be concerned?


Thank you for your guidance!

---

### Post by CharlesA on 2014-04-22
Why did you add all those entries to /etc/modules?

Kernel headers are only needed if you are compiling things and I think the term you are looking for is trying a new kernel.

Perhaps if you were more specific about which devices aren't working, you might get more help.

---

