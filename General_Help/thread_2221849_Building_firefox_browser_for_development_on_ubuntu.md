---
title: "Building firefox browser for development on ubuntu"
date: 2014-05-04
forum: General Help
---

### Post by adityamagadi on 2014-05-04
Hi ppl,
    Am trying to build firefox by following the instructions given here [https://developer.mozilla.org/en-US/docs/Simple_Firefox_build](https://developer.mozilla.org/en-US/docs/Simple_Firefox_build), during the build am running into "virtual memory exhausted error".
i have 2gb of ram and no swap is there any work around to proceed?

---

### Post by Gyokuro on 2014-05-04
Hi

With that low amount of RAM you will never succeed (they are mentioning 2GB RAM + 2GB swap and still problems can occur - I built iceweasel (debian firefox clone) with 32GB RAM and additional swap partition) I think the lowest configuration should be a system with 8GB RAM - you have following options:

1.) add a swap file (8 GB)

or

2.) boot with a live cd and shrink your ubuntu partion and add a swap partition (old rule for swap partitions: double of your system memory but in your case I would go with 8 GB swap partition) and add the swap partition after the first reboot in your /etc/fstab

- HTHT

---

### Post by adityamagadi on 2014-05-04
> **Gyokuro said:**
> Hi

With that low amount of RAM you will never succeed (they are mentioning 2GB RAM + 2GB swap and still problems can occur - I built iceweasel (debian firefox clone) with 32GB RAM and additional swap partition) I think the lowest configuration should be a system with 8GB RAM - you have following options:

1.) add a swap file (8 GB)

or

2.) boot with a live cd and shrink your ubuntu partion and add a swap partition (old rule for swap partitions: double of your system memory but in your case I would go with 8 GB swap partition) and add the swap partition after the first reboot in your /etc/fstab

- HTHT

Hey thanks for the suggestion am gonna try it out now :)

---

