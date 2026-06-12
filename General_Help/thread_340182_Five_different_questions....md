---
title: "Five different questions..."
date: 2007-01-16
forum: General Help
---

### Post by nite owl on 2007-01-16
Hi I've been reading a Linux how-to book all morning and it's left me with a few questions, and probably a few more when I finish reading. Anyway If anyone could answer any of these questions it'd be great. Thanks :)

1) What exactly is the SWAP partition?? And are there any partitions necassary like this for the computer to run correctly?

2) I checked my partition table and I noticed an extended partition, what is this?

3) How would I find out about the current type of hard drive I have (SATA, SCSI, IDE)?

4) and finally is this the way the computer starts up when I turn the power on;

           - Initial RAM disk boots any extra drivers needed to start
           - BIOS starts and retrieves information from the CMOS
           - Then the BIOS boots the OS

Thanks for any help you could give me...actually its four questions lol :)

---

### Post by meng on 2007-01-16
1. Swap partition is hard drive allocation for virtual memory. You can run most (newer) computers fine without a swap partition at all (but I usually make one anyway).
2. There are primary partitions and extended partitions. Extended partitions can have more than one sub-partition inside them (logical partitions). You can have up to four major partitions on a hard disk, but due to extended/logical partitions you can have many more partitions than four.
3. Look at the connections to the hard drive (open up the box). Find a photo of the different connections using google or something.
4. I thought instead of abc as you wrote it, it's bca, but I'm not an expert.

---

### Post by nite owl on 2007-01-16
Thanks for your prompt reply meng, Oh so primary partition's can't have logical partition's inside them, So you create an extended partition if you want to create logical partitions inside it? hmm I'm not sure about four Ill probably have to do some research on the internet and find something if im lucky.

---

### Post by meng on 2007-01-16
Correct. It doesn't make that much difference except for Windows, which insists on being installed to a primary partition. You can install other things (Linux, Linux swaps) to anything, they're not so fussy.

---

