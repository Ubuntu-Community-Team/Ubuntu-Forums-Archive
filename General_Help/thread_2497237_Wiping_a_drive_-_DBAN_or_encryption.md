---
title: "Wiping a drive - DBAN or encryption ??"
date: 2024-04-27
forum: General Help
---

### Post by oygle on 2024-04-27
Have an old Dell laptop, 10 years old, now rettired as it was giving so many problems. So, I usually use DBAN to wipe a drive. It takes a very long time. What about wiping the drive with GParted, then encrypt the whole drive. Won't that be more secure ??

---

### Post by MAFoElffen on 2024-04-28
More secure?

Data wiping standards have evolved over time. Even for DoD data wiping standards.

Magnetic storage standards used to be to fill/write all the blocks with a predetermined binary character, 3-7 times. Later it was found that once is sufficient, and prevents prematurely shortened lifespan, especially on later SSD type drives, where they are built much differently. On almost all SSD's, their firmware has a secure erase feature. Use sparingly.

On Linux, if HDD, why not just use dd to zero-fill the drive? Be careful to specify the 'correct' device.

---

### Post by oygle on 2024-04-28
> **MAFoElffen said:**
> On Linux, if HDD, why not just use dd to zero-fill the drive? Be careful to specify the 'correct' device.

Thanks, it is for a HDD and it is the only drive on that laptop, So this should do the trick

```
$ sudo dd if=/dev/zero bs=1M of=/dev/sda
```

---

### Post by HermanAB on 2024-04-28
If you wish to use the drive again with a Windows machine, then zero fill is best.  Windows will then think that it is a shiny new never used drive. If you are a Linux nerd and like random numbers, use /dev/urandom in the above post.

---

### Post by oygle on 2024-04-28
> **HermanAB said:**
> If you wish to use the drive again with a Windows machine, then zero fill is best.  Windows will then think that it is a shiny new never used drive.

Thanks, but the HDD, having 10 years of usage, it starting to fail.

> **HermanAB said:**
> If you are a Linux nerd and like random numbers, use /dev/urandom in the above post.

Okay, will do. It may take 8 to 10 hours, it's a 1Tb HDD, but that's okay.  :)

---

### Post by oygle on 2024-07-16
As the OS had a few problems, the easiest solution was DBAN. Did a quick erase, then a complete/thorough one. Time to throw the HDD in the e-waste.

---

### Post by currentshaft on 2024-07-16
If you're throwing the device out, DBAN is a waste of time. Take a power drill to the platters instead.

---

### Post by oygle on 2024-07-16
> **currentshaft said:**
> If you're throwing the device out, DBAN is a waste of time. Take a power drill to the platters instead.

A power drill is a waste of time when I can cut it in half with an angle grinder.   :)

---

### Post by ActionParsnip on 2024-07-17
Hammer to the drive and the platters will shatter. Dead easy

---

