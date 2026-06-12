---
title: "Ubuntu Swap Partition - How to wipe or sanitize it?"
date: 2007-01-03
forum: General Help
---

### Post by emarkay on 2007-01-03
Overwriting the data areas is addressed, but I need to investigate a means of wiping the swap partition.  DOD requires:

"c. Overwrite all addressable locations with a single character.
d. Overwrite all addressable locations with a character, its complement, then a random character and verify. THIS METHOD IS NOT APPROVED FOR SANITIZING MEDIA THAT CONTAINS TOP SECRET INFORMATION. "
[http://www.dss.mil/isec/chapter8.htm](http://www.dss.mil/isec/chapter8.htm)


Thank you.
MRK

---

### Post by raul_ on 2007-01-04
you want to remove it? 
try 
```

swapoff <device>

```

then edit the fstab and delete the swap entry.  After that just load the Live CD, run Gparted and delete the partition

Is this what you want?

---

### Post by Falcorian on 2007-01-04
I think he's asking how to make sure that any sensitive information that has been written to swap is not recoverable.

wipe should do it, but I'm not sure on the exact usage, read the man page, although I have no idea what writing random data to the swap will do... Basicly, I THINK wipe should remove any sensitive data that got stored there, but I'm not sure your computer will be happy about you doing it. ;)

---

### Post by az on 2007-01-04
[https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems)

---

### Post by tszanon on 2007-01-04
You could try this:
1. boot the live cd;
2. reformat the swap partition as something else, like EXT2 (not EXT3, because of journaling);
3. now you can easily use anything you want to destroy any data that may yet exist (like rewriting the whole partition and using shred to rewrite again and again);
4. reformat the partition as swap.

After all this, I believe that nothing will be left there.
If the HDD is going to be discarded, just incinerate it. :mrgreen:

---

### Post by emperon on 2007-01-04
Go to [http://www.thc.segfault.net/releases.php]("http://www.thc.segfault.net/releases.php")

There is a tool called secure_delete version 3.1. Download it. Then make and compile. Even if the compilation fails, the tools it generates works fine.

it has 4 tools

sfill : fills your empty disk space (in secure mode 38x random data)
sswap : fills your swap 
smem: fills your memory with chunk of data
srem: deletes a file in a secure way.

I think this is what you wanted. Before wiping swap you need to disable it though.

---

### Post by emarkay on 2007-01-06
> **Falcorian said:**
> I think he's asking how to make sure that any sensitive information that has been written to swap is not recoverable.

wipe should do it, but I'm not sure on the exact usage, read the man page, although I have no idea what writing random data to the swap will do... Basicly, I THINK wipe should remove any sensitive data that got stored there, but I'm not sure your computer will be happy about you doing it. ;)

Correct - will look into wipe - is this a native Linux command or something I need to get from the repositories?

I would prefer not to have to reformat and all that - a command to enter the swap area and overwite with appropriate characters is what is needed.

Oh, and yes enctyption, is not an option, and physical destruction of media is required for TS/SCI data.

Thanks.

---

### Post by OiePoie on 2008-07-23
Disable swap on the partition in question,
usually "swapoff -a" should do the job
overwrite all data on the swap partition with random bits
"dd if=/dev/urandom of=/dev/hda5"
(assuming hda5 is you swap partitions, dont' make any errors at this stage!).
reconfigure the partition for swapping
"mkswap /dev/hda5"
en reenable swapping on the partition
"swapon -a"

---

