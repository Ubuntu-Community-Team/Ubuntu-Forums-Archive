---
title: "Flickering Screen - AMD Turion Dual-Core RM-70 x2 w/ Gallium 0.4 on NVAA"
date: 2017-03-07
forum: General Help
---

### Post by mobileberna on 2017-03-07
I downloaded Ubuntu yesterday because I was given a laptop that had an expired Windows 7 OS. Ubuntu seems like something I really would like to use (even on my phone and tablet), but I am faced with the issue of my screen flickering when I open apps or even when i move my mouse sometimes. I saw that this issue has been fixed before and I was hoping to get help with my flickering screen too!

---

### Post by QIII on 2017-03-07
Hello!

Could you tell us what GPU is installed in the machine?

---

### Post by mobileberna on 2017-03-07
GPU? Gallium 0.4 on NVAA?

---

### Post by QIII on 2017-03-07
That is the driver.

Please post the output of 

```
lspci | grep VGA
```

---

### Post by mobileberna on 2017-03-07
02:00.0 VGA Compatible Controller: NVIDIA Corporation C77 [GeForce 8200M G] (reva2)

---

### Post by QIII on 2017-03-07
My suspicion is that your GPU, introduced in 2007, although supported, may not be up to the task of running Unity.  Unity is a very graphics-greedy desktop environment and your GPU was not intended to be a Maserati among graphics adapters.  It was an entry-level adapter even back then.  The mobile version is likely to be even less muscular.

Although I would suggest waiting for a least a little while to see if anyone comes up with a better idea, you might be better off installing a flavor with a lighter DE such as Xubuntu or Lubuntu.

---

### Post by mobileberna on 2017-03-07
You know what...I was thinking the same thing! The dang card can't even be 1.4 it's freakin 0.4!!! So, how do I go about this? Just google Xubuntu and figure it out?! hahahaha

---

### Post by QIII on 2017-03-07
You can download it from [http://xubuntu.org/](http://xubuntu.org/)

Since Xubuntu is an official flavor of Ubuntu, you can come right back to the Ubuntu Forums with any questions!

---

### Post by mobileberna on 2017-03-07
...any chance you can tell me how to install it? lol!

---

### Post by QIII on 2017-03-07
It installs exactly the same way as Ubuntu -- it uses the same Ubiquity installer.

If you don't have much invested in the Ubuntu install (that is, if you don't have any data to keep), I'd suggest completely re-doing the partitions or using the "Use Entire Disk" option when you get to it.

---

### Post by mobileberna on 2017-03-07
I have nothing invested in Ubuntu. This computer was given to me for free so I'm experimenting with it...I just need to figure out how to install Xubuntu...I shall return!

---

### Post by mobileberna on 2017-03-08
I was not able to find a solution to this issue, so I switched to Lubuntu and no flickering! i do have an issue with Lubuntu, however, that I posted, so please feel free to view my other thread!

---

