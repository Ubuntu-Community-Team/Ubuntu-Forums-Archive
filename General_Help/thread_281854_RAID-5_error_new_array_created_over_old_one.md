---
title: "RAID-5 error: new array created over old one"
date: 2006-10-21
forum: General Help
---

### Post by Rounan on 2006-10-21
Hi,

I had a 5-disk RAID5 array in a machine running breezy, was working fine yesterday.

I've now installed 6.06 server on it. I had some trouble getting the installation routine to recognize the RAID array - by which I mean, it didn't and I gave up.

Now, I can't assemble the array, and it looks like the superblocks have been zeroed:

```
mdadm: No superblock found on /dev/hda (Expected magic 892b4efc, got 00000000)
```

At one point during the installation process, I did instruct the installer to "create an MD device", and gave it the 5 partitions (hd[a,c,e,g,i]1) I wanted it to use. I THOUGHT it would be rebuilding the array, but in retrospect it seems to have re-created an array over the old one.

The old array was clean and I never formatted the new array, so I belive (hope) that the only thing affected was the superblock.

So, what I want to know is: how screwed am I? Can I recover the data somehow?

Thanks,
Rounan

---

