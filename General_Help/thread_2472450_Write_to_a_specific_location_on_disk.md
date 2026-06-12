---
title: "Write to a specific location on disk"
date: 2022-02-27
forum: General Help
---

### Post by michael351 on 2022-02-27
I used dd to wipe a 2TB disk drive which took 20 hours. During this time, the disk had 1 pending sector and 3 reallocated sectors.
This SMART report stayed the same until the very end when the count suddenly jumped 7 reallocated sectors and 0 pending.

I want to use dd again but only at the end of the drive to exercise these sectors (out of curiosity). What syntax do I use to start the read and write process 
1.9 TB into the drive?

dd if=/dev/zero of=/dev/sdb bs=1331072 seek=?(or skip=?) status=progress

thanks!

---

### Post by wyattwhiteeagle on 2022-02-27
> **michael351 said:**
> I used dd to wipe a 2TB disk drive which took 20 hours. During this time, the disk had 1 pending sector and 3 reallocated sectors.
This SMART report stayed the same until the very end when the count suddenly jumped 7 reallocated sectors and 0 pending.

I want to use dd again but only at the end of the drive to exercise these sectors (out of curiosity). What syntax do I use to start the read and write process 
1.9 TB into the drive?

dd if=/dev/zero of=/dev/sdb bs=1331072 seek=?(or skip=?) status=progress

thanks!

First, let's see some report's.

What are your drive's spec's?
Extract this info from...
```
sudo lshw
```
This is easiest done by exporting the entirety to a text file...say...on the desktop and extracting from the text file.

What exactly is the SMART report saying?

Wrap the report's in code tags.

Hopefully, someone with more experience on CLI script line's will chime in.

---

### Post by michael351 on 2022-02-27
I managed to get it to work (a bit of trial and error) using:

dd if=/dev/zero of=/dev/sdb bs=1331072 seek=1427715 status=progress

I chose bs=1331072 as this gave me the fastest write speed (29 MB/s). "Seeking" 1427715 blocks at 1221072 bytes/block put the write start at 1.9 TB where I wanted it. It took less than an hour to write the 100 GB of data.

SMART is reporting that I had 8 sectors reallocated. No sectors pending. I ran the above 'dd' command a couple of times and the reallocated sector count remain unchanged. This disk is being used to store old work data (30% of the drive) as an emergency backup offline and powered off.

---

### Post by wyattwhiteeagle on 2022-02-27
> **michael351 said:**
> I managed to get it to work (a bit of trial and error) using:

dd if=/dev/zero of=/dev/sdb bs=1331072 seek=1427715 status=progress

I chose bs=1331072 as this gave me the fastest write speed (29 MB/s). "Seeking" 1427715 blocks at 1221072 bytes/block put the write start at 1.9 TB where I wanted it. It took less than an hour to write the 100 GB of data.

SMART is reporting that I had 8 sectors reallocated. No sectors pending. I ran the above 'dd' command a couple of times and the reallocated sector count remain unchanged. This disk is being used to store old work data (30% of the drive) as an emergency backup offline and powered off.

Is that your main goal?
If so, please detail how you accomplished your goal and mark this thread as 'solved.'

---

