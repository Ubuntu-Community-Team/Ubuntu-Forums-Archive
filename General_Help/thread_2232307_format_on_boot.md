---
title: "format on boot"
date: 2014-07-01
forum: General Help
---

### Post by Istvan D on 2014-07-01
Hi folks,

I have a question I couldn't find an answer yet: is it possible to set up a configuration (fstab, script, whatever), so the Ubuntu (or Linux in general) always formats a drive at boot? For explanation, here is my situation: I have a 120GB SSD with 3 OS's: Ubuntu, Win and OS X. I have a 4GB hda6 partition, which is my swap. My idea: I would use it as swap under Ubuntu, but for the page file under OS X. But for that, I have to reformat it each time I start up the laptop, at a pretty early stage of boot.
Has anyone experience with such stuff? Thanks in advance

---

### Post by sudodus on 2014-07-01
I haven't done exactly what you want, but similar tasks. If there is no entry in fstab, you can use ***mkswap*** to create linux-swap in that partition and after that use ***swapon*** to start using it.

Swapping in an SSD will be fast compared to a HDD, but it will increase wear, and SSDs have a shorter lifetime (number of write operations) compared to HDDs, even if it is improving and much better than a couple of years ago. Maybe a swap file is better, because it can be wiped and the SSD can be 'cleaned' with discard and the next time the swapfile will be localized somewhere else, which will spread the wear. Or even better would be to swap to RAM (if there is enough of it) for example using zRAM. I don't know if there are such options for OS X.

---

