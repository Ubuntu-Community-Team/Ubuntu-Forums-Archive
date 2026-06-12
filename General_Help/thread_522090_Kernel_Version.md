---
title: "Kernel Version"
date: 2007-08-10
forum: General Help
---

### Post by timohnani on 2007-08-10
Hi,

I am quite new to Linux and I have a question about kernel versions. I installed Kubuntu on my laptop. When I start it up I am given the options of 2.6.20-15-Generic and 2.6.20-16-Generic in grub. Usually I choose the 16 one. 

Then when I installed Kubuntu on my laptop I was offered 2.6.20-15 only in grub. 

My first question is, what are the differences between the 2 versions?

Why did the 16 version get installed on my laptop and the 15 version on my desktop?

Why does my laptop give me 2 options? 

How can I make my desktop into version 16 if its better?

How can I remove the second option from my laptop if necessary?


Can anyone help? :confused:

Timo

---

### Post by ayoli on 2007-08-10
> **timohnani said:**
> Hi,

I am quite new to Linux and I have a question about kernel versions. I installed Kubuntu on my laptop. When I start it up I am given the options of 2.6.20-15-Generic and 2.6.20-16-Generic in grub. Usually I choose the 16 one. 

Then when I installed Kubuntu on my laptop I was offered 2.6.20-15 only in grub. 

My first question is, what are the differences between the 2 versions?
between minor updates like that, differences are, most of the time, security fixes or bug fixes
> 
Why did the 16 version get installed on my laptop and the 15 version on my desktop?
your desktop may need an upgrade
> 
Why does my laptop give me 2 options? 
because you have now two kernels
> 
How can I remove the second option from my laptop if necessary?
If the new one (-16) works fine for you, you can safely remove the older one.This will update choices at at boot and also save some sapce on your hdd.
To remove it, type in a terminal:
```
sudo apt-get remove linux-image-2.6.20-15-generic 
```
(you will be prompted for your user password)

---

### Post by timohnani on 2007-08-11
HI,

Thanks for the info. How would I go about upgrading from 15 to 16?

Timo

---

### Post by ayoli on 2007-08-11
> **timohnani said:**
> HI,

Thanks for the info. How would I go about upgrading from 15 to 16?

Timo

```
sudo apt-get update && sudo apt-get dist-upgrade
```
should do the trick

---

