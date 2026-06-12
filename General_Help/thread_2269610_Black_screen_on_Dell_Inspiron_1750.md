---
title: "Black screen on Dell Inspiron 1750"
date: 2015-03-17
forum: General Help
---

### Post by pipsy17 on 2015-03-17
As mentioned I am using a Dell Insiprion 1750 which is currently running Ubuntu 14.04.02 LTS. I cannot see any "purple" screen on boot up and unable  view the grub screen when holding shift. I can however ssh into the machine.  Things I have tried is booting in nomodeset and tried changing brightness via setpci. Problem occurred after opening the lid. Any help diagnosing and resolving this issue would be appreciated.

---

### Post by carl4926 on 2015-03-17
Did you try rebooting it
You should be able to do that via ssh

---

### Post by pipsy17 on 2015-03-17
> **carl4926 said:**
> Did you try rebooting it
You should be able to do that via ssh

Yea, that was the first thing I did. That was how I discovered I couldn't see the "purple" screen or view the grub menu. Regardless, I should've mentioned that.

---

### Post by carl4926 on 2015-03-17
What graphics (GPU) are involved
You could run 
```
sudo apt-get update
```
then
```
sudo apt-get dist-upgrade
```
all via ssh and see if that improves matters

---

### Post by pipsy17 on 2015-03-17
> **carl4926 said:**
> What graphics (GPU) are involved
It is called "Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller" according to lspci. 
However, [engadget ]("http://www.engadget.com/products/dell/inspiron/1750/specs/")labels it as an Intel (GMA) X4500HD so I am assuming they are synonymous. 
> 
You could run...see if that improves matters
Unfortunately, this did not work. Take note that I rebooted after both the update and upgrade were done.

---

### Post by mörgæs on 2015-03-17
With this graphics processor I suggest L/Xubuntu.

---

### Post by pipsy17 on 2015-03-17
> **mörgæs said:**
> With this graphics processor I suggest L/Xubuntu.

So your implying that the resolution to this problem is to just cut my losses and format my current install so Xubuntu can be installed? which is not a horrible idea ,but, if avoidable I would prefer not to.

---

