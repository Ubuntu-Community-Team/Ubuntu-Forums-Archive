---
title: "Is There a TimeDelay, Slow To Execute Input Requests"
date: 2021-09-30
forum: General Help
---

### Post by wyattwhiteeagle on 2021-09-30
Every click or double-click or right-click I'm noticing something like a 15 to 20 second time delay before anything happens.

What is going on and how do I optimize for faster executions?

---

### Post by guiverc on 2021-09-30
How much RAM do you have? and have you allocated a swap partition/swapfile?

Depending on how you installed your system, you may not have any *swap *active.

I'll provide some links

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

you can do a quick check using the command `free -h`  (you'll find an example of this in the second link I provided ie. *link written for 20.04 & 20.10*).  On my box I get

```
guiverc@d960-ubu2:/de2900/ubuntu_64$   free -h
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       5.0Gi       628Mi       124Mi       2.0Gi       2.2Gi
Swap:          9.5Gi       4.1Gi       5.5Gi
```

with the Swap line giving me details of swap available (*via swap partition and/or swapfile*)

If you second line is 0's as per the second provided link example, adding a swapfile may help resolve your issue (and make your box more responsive when RAM is getting filled)

(*a couple of development cycles ago I needed to steal 4GB from a box for testing  in another box that had hardware issues; I didn't think I'd notice the halved  RAM; but I sure did; at least I did until I activated swap that the box didn't have setup*).

---

### Post by wyattwhiteeagle on 2021-09-30
> **guiverc said:**
> How much RAM do you have? and have you allocated a swap partition/swapfile?

Depending on how you installed your system, you may not have any *swap *active.

I'll provide some links

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)

- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

you can do a quick check using the command `free -h`  (you'll find an example of this in the second link I provided ie. *link written for 20.04 & 20.10*).  On my box I get

```
guiverc@d960-ubu2:/de2900/ubuntu_64$   free -h
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       5.0Gi       628Mi       124Mi       2.0Gi       2.2Gi
Swap:          9.5Gi       4.1Gi       5.5Gi
```

with the Swap line giving me details of swap available (*via swap partition and/or swapfile*)

If you second line is 0's as per the second provided link example, adding a swapfile may help resolve your issue (and make your box more responsive when RAM is getting filled)

(*a couple of development cycles ago I needed to steal 4GB from a box for testing  in another box that had hardware issues; I didn't think I'd notice the halved  RAM; but I sure did; at least I did until I activated swap that the box didn't have setup*).

My RAM/Swap Spec's...

```
wyatt@wyatt-aspiree1532:~$ free -h
              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       575Mi       5.9Gi       185Mi       1.2Gi       6.7Gi
Swap:         7.8Gi          0B       7.8Gi
```

---

