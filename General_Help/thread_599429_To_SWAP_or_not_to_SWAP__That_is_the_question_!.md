---
title: "To SWAP or not to SWAP ? That is the question !"
date: 2007-11-01
forum: General Help
---

### Post by Spear on 2007-11-01
Hi,

A few weeks ago, i read another of these articles about the real utility of SWAP considering the size of memory on computers novadays.

Then it came to my mind ... like it did a few years ago ... has SWAP a real use on a computer with 2 GB of memory ? Do we finally put a SWAP partition just because we're used to, and that considering the size of our hard drives, we do this because it won't cost much space, and " in case of " it could be of some use ?

What's your opinion ?

Secondarily, a thing i didn't know, i learned a few days ago that SWAP could be in a single file instead of a dedicated partition (like in Windows in fact). I'm so surprised i never heard about it before : is the "SWAP in a file" solution such a bad solution or is it so little known compared to the good old " SWAP partition " ?

There again, i'd like to talk about it with the community.

Have a great day !

---

### Post by mahousaru on 2007-11-01
Depends on your situation.  Even with my 2GB of memory I still have 4GB swap because HDD is cheap and if I don't want to swap I can turn it off.  Of course if I do want swap and I didn't create one, then I will need to go for a file which is not as efficient as a partition (I hear things have improved with the latest distros), or I would have to rejig my partitions.

I would not swap if I had plenty of ram but was either lacking in HDD, or lacking in writes to the storage media.  Thinking about the solid-state eeepc or the Zaurus here.  I killed a SD card in a Zarus within a month when I turned on swapping. 

Will be interested if anyone has any hard info on swap files v swap parts all my info is based on IRC/pub chatter.

---

### Post by ddrichardson on 2007-11-01
Swap files are an awful idea compared to a partition - consider fragmentation (I know this isn't such an issue in Linux because of the way files are distributed).

Actually, it's perfectly possible to use a swap partition in Windows, I have one on my Win2k box.

---

### Post by kerry_s on 2007-11-01
i have no swap, i use "swapd" which creates swap files when needed and deletes them when no longer needed. i only have 256ram, but i use a custom install, it's built for speed.

---

### Post by apfsdsdu on 2007-11-01
I have 4 GB of memory and a small swap partition. It's pretty much always unused. I tried to get the system to actually write something on the swap partition by opening a million billion tabs in Firefox, and eventually it did. There wasn't really a real need for it even then, about a gigabyte of the memory was still used for disk cache.

---

### Post by mahousaru on 2007-11-01
> **apfsdsdu said:**
> I have 4 GB of memory and a small swap partition. It's pretty much always unused. I tried to get the system to actually write something on the swap partition by opening a million billion tabs in Firefox, and eventually it did. There wasn't really a real need for it even then, about a gigabyte of the memory was still used for disk cache.

Ah the actual size of the swap.  That chestnut brings back memories of many heated discussions.  I used to advocate smaller swaps because if the system is swapping so much something is wrong and it would be dog slow.  Then someone pointed out to me that the swap is also used for things like hibernation and that is one of the main reasons why it should be 2 x main memory.

---

### Post by Ramorous on 2007-11-01
I administer several servers with over 10gb of ram each. I do create a 6g swap partition only as a failsafe. It is never used. The costs of HDDs nowadays and the size of them make it inexpensive to create small swap partition.

---

### Post by bingoUV on 2007-11-01
kerry_s,
    How does this swapd handle hibernation? If I have applications worth 1 GB memory open when I hibernate, where will it create swap files? I am told that current implementations of hibernate in linux do not support compression.

---

### Post by kerry_s on 2007-11-01
> **bingoUV said:**
> kerry_s,
    How does this swapd handle hibernation? If I have applications worth 1 GB memory open when I hibernate, where will it create swap files? I am told that current implementations of hibernate in linux do not support compression.

it don't, you need a dedicated swap partion for hibernation/sleep. i don't use those.

---

