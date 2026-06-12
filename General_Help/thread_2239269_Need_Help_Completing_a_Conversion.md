---
title: "Need Help Completing a Conversion"
date: 2014-08-12
forum: General Help
---

### Post by ewangr on 2014-08-12
Situation is that before 14.04 came out I had two Win 8 machines (one downstairs in the family room, one upstairs in ours) that each had a USB 3 raid-0 array attached. After 14.04 came out I setup the upstairs machine with it, and have been very pleased. So now I'm thinking of completing the conversion, but have a couple issues/questions.

1) Instead of keeping the two USB 3 RAID-0 arrays as NTFS I would like to convert one and then the other to a Linux file system. I've heard DMRAID might work for this? Anyone who can confirm? I presume I use that to setup the 4 disks as an array and then use ZFS or ext-4 to format them as a large partition?

2) Similarly I have been using Win 8 shares to copy files back and forth. What is the Linux equivalent?

3) Until today I couldn't convert the downstairs machine because of Netflix. Was happy to see the "fix" listed elsewhere in the forums (DEV version of chrome and libs) and have already tested on the upstairs machine. However I'm wondering if there is any reason to think Netflix or Google would change things to cause this to stop working?

Thanks in advance!

---

### Post by TheFu on 2014-08-13
[http://blog.jdpfu.com/Lin_4_Win_Users](http://blog.jdpfu.com/Lin_4_Win_Users) - I think you need to start here to get an overview and some terms.

USB - don't use it for RAID anything. RAID0 is dangerous and only useful for people needing temporary storage. It risks complete data loss across all drives if 1 fails. You can merge 2 file systems into 1 using lots of other Linux tools or even symlinks.

I wouldn't touch ZFS. Might consider btrfs, if I really needed pools.  I'd have a solid, working, know-to-always-works, backup setup, however.

Samba is the normal way to allow Windows systems access to Linux storage over the network. There are too-many how-to guides, so don't get confused and stick with 1. For simple sharing needs, the **how-to geek** instructions are good. Samba can be extremely complex - don't get lost.

Google and Netflix are corporations. They will do "whatever they want, when they want, to enhance shareholder value." That is their mission, regardless of any catchy motto.  Netflix has been broken on Linux for most of the time. If there isn't stated support for Linux users, it isn't **any** concern to them at all. If it happens to work today, feel lucky. Netflix gets pushed around by media houses all the time - if one of them decides that Linux has become easy to pirate their content, they could change the contract to become hostile towards Ubuntu/Linux at any point.  Just look at "Ultraviolet" - how consumer-hostile is that technology?

---

### Post by ewangr on 2014-08-13
> **TheFu said:**
> USB - don't use it for RAID anything. RAID0 is dangerous and only useful for people needing temporary storage. It risks complete data loss across all drives if 1 fails. You can merge 2 file systems into 1 using lots of other Linux tools or even symlinks.

I have been using USB external drives with RAID 0 since 2009 and had no data issues that weren't the result of a hard drive failing. That is why I have two systems that I keep in sync so that if one goes down I have all my data backed up on the other. It is much cheaper to buy/build two 12TB arrays externally than to build them internally, and much easier to get at a failed drive.

> Samba is the normal way to allow Windows systems access to Linux storage over the network.

Yes, I know. That's what I'm using currently. What I am asking is when both machines are Linux boxes how to I see the drive attached to box 1 from box 2? NFS?

> Google and Netflix are corporations. They will do "whatever they want, when they want, to enhance shareholder value." That is their mission, regardless of any catchy motto.  Netflix has been broken on Linux for most of the time. If there isn't stated support for Linux users, it isn't **any** concern to them at all. If it happens to work today, feel lucky. Netflix gets pushed around by media houses all the time - if one of them decides that Linux has become easy to pirate their content, they could change the contract to become hostile towards Ubuntu/Linux at any point.  Just look at "Ultraviolet" - how consumer-hostile is that technology?

I fully agree that Netflix and Google have their evil sides to them, and am certainly no fan of DRM. On the other hand, given that the two seem to be working together to support Chrome OS because neither of them likes depending on Microsoft it seems that the chances of them continuing to support Chrome is greater than 0. Was hoping someone who might be closer to what is going on might be able to comment.

---

### Post by TheFu on 2014-08-13
> **ewangr said:**
> I have been using USB external drives with RAID 0 since 2009 and had no data issues that weren't the result of a hard drive failing. That is why I have two systems that I keep in sync so that if one goes down I have all my data backed up on the other. It is much cheaper to buy/build two 12TB arrays externally than to build them internally, and much easier to get at a failed drive.

On linux?  RAID is a different animal than on Windows.
I agree that USB-connected storage is easier and usually less expensive, but it brings with it other issues - mainly due to poor driver support. I still have a USB3 hub that doesn't work with Linux except in USB2 mode - and a USB3 card that has been failing due to loose ports.  Both USB2/3 have queuing issues on Linux, so I'd never put any RAID on them. Haven't tested this on newer kernels, so it may be fixed. Should know this week.  I've never had any issue with eSATA or Infiniband connections - those are solid.

Staying in sync without RAID0 is relatively easy. rsync or 20 other software methods. RAID0 with multiple different RAID-sets is just **scary** - now any failing drive in any RAID-set can lead to a bad day. I'd much rather merge file systems outside RAID - lots of tools do that. Check out brtrfs, unionfs, aufs, lvm, mhddfs, glusterfs, etc ... or even just synlinks.

> **ewangr said:**
> Yes, I know. That's what I'm using currently. What I am asking is when both machines are Linux boxes how to I see the drive attached to box 1 from box 2? NFS?
Sorry - missed that in the OP.  CIFS, NFS, sshfs, rsync, 20 others.  For Linux-to-Linux connectivity over wired ethernet, I use NFS with hard mounts.  If there is any question about the connectivity, I use NFS-soft mounts and live with the repercussions. The other options are for special needs - clustering, WAN-storage replication, etc...

> **ewangr said:**
> I fully agree that Netflix and Google have their evil sides to them, and am certainly no fan of DRM. On the other hand, given that the two seem to be working together to support Chrome OS because neither of them likes depending on Microsoft it seems that the chances of them continuing to support Chrome is greater than 0. Was hoping someone who might be closer to what is going on might be able to comment.

Google and Netflix have fairly clear employee non-disclosure agreements. If you know anyone working there, then you know they don't talk about their work much. I've worked at places like that. We didn't talk.

Anyway, I couldn't review the OP when writing this - forum failure. Hope it helps and provides options.

---

