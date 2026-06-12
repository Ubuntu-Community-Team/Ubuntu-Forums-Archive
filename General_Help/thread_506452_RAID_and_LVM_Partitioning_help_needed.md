---
title: "RAID and LVM Partitioning help needed"
date: 2007-07-21
forum: General Help
---

### Post by Crashmaxx on 2007-07-21
I'm looking to start using my desktop box as a server and MythTV box. Basically, I will leave it on all the time and have it act as a PVR and such, in addition to using it normally. I already have a 250GB Seagate hard drive in it and have another identical drive in my home server that I am "decommissioning", so to speak. So I am putting that drive in my desktop and am going to have at least / and swap be RAID 1 and the rest of the space I want to have be an XFS partition for TV and other large files, most of which of little real value.

So the first question is, can I RAID 1 an entire disk and just have that array act as my physical drive and just copy my partitions to it? I think that would be easiest and if I can then do it that simply then it is worth losing some space to have everything mirrored and at least safe from disk failure.

If that's not possible, then the next best thing I was thinking was having a / partition that is RAID 1 and a swap also RAID 1 and the rest of the space be a LVM volume group. That way I can have the XFS partition act like one big 400GB partition, and easily add far more space to just this partition. But what would happen if I lost a disk? Would I just lose half the data? Or would all of it be corrupted? And can the partition still work at all with part of it gone?

Lastly, I currently have a separate /home partition that consumes most of my drive. I'm not sure if I want to keep it, especially in the second scenario, I would prefer to just keep my files on the RAID 1 / then have them on the LVM. Any advise how to at least resize the partition or move the data and get rid of it all together?

I hope you get the idea of what I am trying to accomplish and someone has some good advice. I have used RAID and LVM before but am not very familiar still so anything step by step would be great. Thanks.

---

### Post by Ocxic on 2007-07-21
RAID 1 give disk faulire protection, if one disk fails all your data will still be there, it basicall makes a 1:1 copy between the two disks.

you shouls be able to just copy your partitons that you want, some re-configureing may be nessaccery to do that, but i don't see it as a big problem

RAID and LVM are basically 2 different ways of doing the same thing, RAID being better if you want data protection, I wouldn't recommends using RAID and LVM at the same time,

---

