---
title: "question about imaging a hard drive"
date: 2019-05-06
forum: General Help
---

### Post by Buntu Bunny on 2019-05-06
From the Community Help Wiki, DataRecovery -

> To recover data from a failed device, you will need another device of equal or greater storage onto which to save your data. If you need to make an image of the failed device, you will need yet another quantity of space.

I assume this refers to the total size of the hard drive, or does it refer to the amount of data on it? I have a 1TB HDD that's barely a quarter full. Most of it I backed up, but I'd still like to take a look-see. I'm not sure there's enough on it, however, to warrant buying a 2TB HDD just to see. Hence my question.

---

### Post by HermanAB on 2019-05-06
Well, what is the problem that you actually have?

If you have a failing 1TB drive that you wish to try and recover data from, then you need a 1TB or larger drive to copy it to, otherwise the resulting file system will be corrupted.

Running a recovery program such as ddrescue on the failing drive, will not work well, since it is faulty...

If the faulty drive is totally buggered, then you can try to buy an exact same old drive on Ebay and swap the drive controller card to try and get it to spin up again.

---

### Post by Buntu Bunny on 2019-05-06
> **HermanAB said:**
> Well, what is the problem that you actually have?

If you have a failing 1TB drive that you wish to try and recover data from, then you need a 1TB or larger drive to copy it to, otherwise the resulting file system will be corrupted.

Running a recovery program such as ddrescue on the failing drive, will not work well, since it is faulty...

If the faulty drive is totally buggered, then you can try to buy an exact same old drive on Ebay and swap the drive controller card to try and get it to spin up again.

The problem was that the HDD stopped booting - black screen (on a 16-month old Dell computer). I replaced the hard drive with a new one and tried the old one in a hard drive external enclosure with no success. Then I tried a USB to SATA converter, also no joy. I can hear the disk spinning when I turn either of these devices on. The only other possibility seems to be imaging, but I didn't want to have to buy a 2TB disk if a 1TB would do, hence my original question. It's been awhile since all this happened, but I found the HDD the other day and couldn't help but wonder if I could still take a look at it.

---

### Post by HermanAB on 2019-05-06
OK, then you could try to revive it by swapping the drive controller board with one from another identical drive.

---

### Post by CatKiller on 2019-05-06
> **Buntu Bunny said:**
> I assume this refers to the total size of the hard drive, or does it refer to the amount of data on it? I have a 1TB HDD that's barely a quarter full.

It depends on the method that you're using, which is what the wiki is - clumsily - saying. If you want to copy the files, you need enough space to hold the copy of the files. If you want to take an image of the disc you need enough space to hold the image of the disc.

> **Buntu Bunny said:**
> The problem was that the HDD stopped booting - black screen (on a 16-month old Dell computer). I replaced the hard drive with a new one and tried the old one in a hard drive external enclosure with no success. Then I tried a USB to SATA converter, also no joy. I can hear the disk spinning when I turn either of these devices on. The only other possibility seems to be imaging, but I didn't want to have to buy a 2TB disk if a 1TB would do, hence my original question. It's been awhile since all this happened, but I found the HDD the other day and couldn't help but wonder if I could still take a look at it.

It's not worth doing. If the disc is so knackered that it can't be read enough to mount it, then you'd need to modify the disc itself, as HermanAB says. You've still got the stuff that you backed up.

---

### Post by Buntu Bunny on 2019-05-06
HermanAB and Catkiller, thank you. That gives me an idea of what to try.

---

