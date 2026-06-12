---
title: "Dead XFS Superblock"
date: 2007-10-30
forum: General Help
---

### Post by ACA:Sleeper on 2007-10-30
I have two arrays in my Ubuntu 7.10 64bit system, a 2x200gb raid0 and a 3x320gb raid5. Both use mdadm and lvm2 with XFS.

Part of the reason I went with this setup was the options of online capacity expansion and even raid level migration. So, the time comes, I'm out of space, and I grab another 320gb drive to add to my raid5 array. I'm not a big one for backing up.... but I thought this was a bit risky, so, the family photos and a videos get copied to the raid0 array, just while I integrate the new drive.

During the copy of data (~60GB) the system freezes, and although I have not had this happen in quite some time, it used to happen pretty regularly when moving data en-mass. So... hard reset.

Boot back up.... raid0 is GONE.... mount point shows nothing. So, I look... /proc/mdstat show no issues. However xfs_repair said the following...


> root@sleeping-giant:/# xfs_repair /dev/md1
xfs_repair: warning - cannot set blocksize on block device /dev/md1: Device or resource busy
- creating 4 worker thread(s)
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...
.................................................. ............................................
.................................................. ............................................
<snip many more lines of dots>
.................................................. ............................................
.................................................. ............................................
Sorry, could not find valid secondary superblock

Now, I wish I had all my data backed up, but I don't, so although my raid0 array was full of 'less important' stuff, it's still very hard to replace 300+GB of data.

Anyone have any clue what to try next?
I really don't want to write the data off as lost.
Any good recovery programs....?

I'm also interested in WHY it happened... I read bits and peices, could it be the drives write buffer overloading??

---

### Post by fjgaude on 2007-10-31
I guess you tried to re-assemble the array, eh? Like so:

```
sudo mdadm --assemble --scan --verbose
```

mdadm will find the array and put it back together if nothing is broken.

What does 

```
sudo mdadm -D /dev/md0
```

show?

---

