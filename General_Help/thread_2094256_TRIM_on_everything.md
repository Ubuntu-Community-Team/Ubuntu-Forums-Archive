---
title: "TRIM on everything?"
date: 2012-12-13
forum: General Help
---

### Post by NertSkull on 2012-12-13
So, I have a question about TRIM.  If I've read correctly, I have it enabled on my SSD.  But do I need it enabled on the SWAP partition?  I also have my /boot on a separate partition, do I need to enable TRIM on that somehow?

I read somewhere that those partitions also need it.  But I'm not sure.

My question gets more complicated also.  I have full disk-encryption set up.  So I have TRIM enabled (discard) in my fstab and my crypttab.

I have an encrypted container, within which has logical volumes for my root drive and my swap space.  

In crypttab, there is only one entry for the encrypted container.  So I added discard to that.

But in my fstab, I only added "discard" to my root drive.  Is that a problem?  Do I need to add it to swap space.

What about boot?  Its not encrypted, but its still on the SSD.  I know it isn't used much, but would it still be wise to use TRIM (discard) on it as well?

So, TL;DR -- Do I need TRIM enabled on SWAP or /boot partitions?  And second, if I have full-disk encryption, do I need to enable TRIM on all logical volumes, or is enabling it in crypttab enough?

---

### Post by haqking on 2012-12-13
> **NertSkull said:**
> So, I have a question about TRIM.  If I've read correctly, I have it enabled on my SSD.  But do I need it enabled on the SWAP partition?  I also have my /boot on a separate partition, do I need to enable TRIM on that somehow?

I read somewhere that those partitions also need it.  But I'm not sure.

My question gets more complicated also.  I have full disk-encryption set up.  So I have TRIM enabled (discard) in my fstab and my crypttab.

I have an encrypted container, within which has logical volumes for my root drive and my swap space.  

In crypttab, there is only one entry for the encrypted container.  So I added discard to that.

But in my fstab, I only added "discard" to my root drive.  Is that a problem?  Do I need to add it to swap space.

What about boot?  Its not encrypted, but its still on the SSD.  I know it isn't used much, but would it still be wise to use TRIM (discard) on it as well?

So, TL;DR -- Do I need TRIM enabled on SWAP or /boot partitions?  And second, if I have full-disk encryption, do I need to enable TRIM on all logical volumes, or is enabling it in crypttab enough?

swap shouldnt be on a SSD if you can help it, and wont support discard anyway

---

### Post by NertSkull on 2012-12-13
I don't know, everything I've read about that is about the argument  that its not cost-efficient to do.  Right now I have a 240 GB SSD with 8 gigs of RAM.  My swap effectively never gets used, except for when I put the computer into hibernation.  And its easier to set up single passphrase unlocking encryption by just encrypting the drive, and making a 10 gig logical volume swap partition within the encrypted container, and leave the other 200+ gigs as the root drive.

I know its not considered by many to be ideal to put swap on the SSD.  But 8 gigs of RAM is enough for what I do that it never gets used except in hibernate mode.  But I could definitely be wrong about all that and maybe SWAP on SSD destroys the drive in a way I'm unaware of.

So that's why I'm wondering if TRIM should be enabled, but it appears you say it won't support it anyway.  So that's good to know.

But even so, what about boot?

---

### Post by haqking on 2012-12-13
> **NertSkull said:**
> I don't know, everything I've read about that is about the argument  that its not cost-efficient to do.  Right now I have a 240 GB SSD with 8 gigs of RAM.  My swap effectively never gets used, except for when I put the computer into hibernation.  And its easier to set up single passphrase unlocking encryption by just encrypting the drive, and making a 10 gig logical volume swap partition within the encrypted container, and leave the other 200+ gigs as the root drive.

I know its not considered by many to be ideal to put swap on the SSD.  But 8 gigs of RAM is enough for what I do that it never gets used except in hibernate mode.  But I could definitely be wrong about all that and maybe SWAP on SSD destroys the drive in a way I'm unaware of.

So that's why I'm wondering if TRIM should be enabled.

But even so, what about boot?

swap wont support TRIM anyways.

/boot is hardly written too so redundant and should probably be ext2 aswell and mount /tmp to RAM

---

### Post by NertSkull on 2012-12-13
I didn't realize that ext2 doesn't really support trim.  But my boot is mounted as ext2, so TRIM is not needed there.

Thanks for the help, it makes more sense now.

---

### Post by haqking on 2012-12-13
> **NertSkull said:**
> I didn't realize that ext2 doesn't really support trim.  But my boot is mounted as ext2, so TRIM is not needed there.

Thanks for the help, it makes more sense now.


Ext2 does support trim but not fully, no point doing it for /boot as it is hardly written too.

/boot should be ext2 typically as journalling/overhead is not required

EXT4 supports TRIM fully

If i was you, use TRIM for /HOME and / and mount /tmp to RAM.

For example here is my FSTAB

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2e19524f-b028-4ef3-93a5-bed6757708fc /               ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro **       0       1
# /DATA was on /dev/sdc1 during installation
# UUID=3A2084D220849713 /DATA           ntfs    defaults,umask=007,gid=46 0       0
# /SSD2DATA was on /dev/sdb1 during installation
UUID=de961735-1d84-4c72-8abe-fefa7b03a708 /SSD2DATA       ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro**        0       2
# /home was on /dev/sda2 during installation
UUID=5a71aee7-cd8c-431f-bdc3-828bc40226b7 /home           ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro **       0       2
# swap was on /dev/sdc2 during installation
UUID=c01746dc-7f90-40a6-9dda-324aecf9bdce none            swap    sw              0       0
# Place tmp into ram
[B]tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
tmpfs       /var/tmp    tmpfs       defaults,mode=1777      0   0
tmpfs       /var/spool  tmpfs       defaults,mode=1777      0   0
tmpfs       /var/cache  tmpfs       defaults                0   [/B]0
```

Optimised for SSD

---

### Post by Pjotr123 on 2012-12-13
Here's a complete how-to for tuning an SSD:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Notes:
- Don't put /var/tmp in tmpfs in RAM, as /var/tmp is meant for temporary files that need to survive a reboot;
- A swap partition will be trimmed automatically, upon mounting at each boot. No tuning necessary.

---

### Post by bab1 on 2012-12-13
> **Pjotr123 said:**
> ...
Notes:
- Don't put /var/tmp in tmpfs in RAM, as /var/tmp is meant for temporary files that need to survive a reboot;
Where did you get that idea?  Can you please document that?  I'm curious to see the logic.

My understanding was that /tmp will NOT survive either a warm or cold boot.  I just restarted my machine (@ 11:51) and nothing survived.  See ```
drwx------ 2 bab bab 4096 2012-12-13 11:51 keyring-G7BRQT
drwx------ 2 bab bab 4096 2012-12-13 11:55 orbit-bab
drwx------ 2 gdm gdm 4096 2012-12-13 11:51 orbit-gdm
drwx------ 2 bab bab 4096 2012-12-13 11:51 pulse-2hO62oopsgCl
drwx------ 2 bab bab 4096 2012-12-13 11:51 ssh-JufHfP1511
drwx------ 2 bab bab 4096 2012-12-13 11:51 virtual-bab.TegvC3

```

---

### Post by haqking on 2012-12-13
> **bab1 said:**
> Where did you get that idea?  Can you please document that?  I'm curious to see the logic.

My understanding was that /tmp will NOT survive either a warm or cold boot.  I just restarted my machine (@ 11:51) and nothing survived.  See ```
drwx------ 2 bab bab 4096 2012-12-13 11:51 keyring-G7BRQT
drwx------ 2 bab bab 4096 2012-12-13 11:55 orbit-bab
drwx------ 2 gdm gdm 4096 2012-12-13 11:51 orbit-gdm
drwx------ 2 bab bab 4096 2012-12-13 11:51 pulse-2hO62oopsgCl
drwx------ 2 bab bab 4096 2012-12-13 11:51 ssh-JufHfP1511
drwx------ 2 bab bab 4096 2012-12-13 11:51 virtual-bab.TegvC3

```

it is defined in the FHS [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard ]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

> var/tmp   Temporary files to be preserved between reboots.

/var/tmp is different to /tmp

---

### Post by bab1 on 2012-12-13
> **haqking said:**
> it is defined in the FHS [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard ]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")



/var/tmp is different to /tmp

Ahhhh, I missed the /var part.  My mistake.  :(

---

### Post by Cheesemill on 2012-12-13
> **haqking said:**
> ```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2e19524f-b028-4ef3-93a5-bed6757708fc /               ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro **       0       1
# /DATA was on /dev/sdc1 during installation
# UUID=3A2084D220849713 /DATA           ntfs    defaults,umask=007,gid=46 0       0
# /SSD2DATA was on /dev/sdb1 during installation
UUID=de961735-1d84-4c72-8abe-fefa7b03a708 /SSD2DATA       ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro**        0       2
# /home was on /dev/sda2 during installation
UUID=5a71aee7-cd8c-431f-bdc3-828bc40226b7 /home           ext4    **defaults,noatime,nodiratime,discard,errors=remount-ro **       0       2
# swap was on /dev/sdc2 during installation
UUID=c01746dc-7f90-40a6-9dda-324aecf9bdce none            swap    sw              0       0
# Place tmp into ram
[B]tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
tmpfs       /var/tmp    tmpfs       defaults,mode=1777      0   0
tmpfs       /var/spool  tmpfs       defaults,mode=1777      0   0
tmpfs       /var/cache  tmpfs       defaults                0   [/B]0
```
There is no need to specify noatime ***and*** nodiratime.

Just using noatime implicitly specifies nodiratime as well.

---

### Post by haqking on 2012-12-13
> **Cheesemill said:**
> There is no need to specify noatime ***and*** nodiratime.

Just using noatime implicitly specifies nodiratime as well.

Spookily enough I was reading an article this evening which was saying the same, I hadnt realised it was a subset, but i am finding conflicting information.

I am still looking into it, but cheers.

---

### Post by Cheesemill on 2012-12-13
You may want to look [here]("http://lwn.net/Articles/245002/") where someone looks at the source code.

---

### Post by haqking on 2012-12-13
> **Cheesemill said:**
> You may want to look [here]("http://lwn.net/Articles/245002/") where someone looks at the source code.

ha, yeah i already had it open in a tab ;-)

Cheers

---

### Post by dcstar on 2012-12-14
> **haqking said:**
> swap shouldnt be on a SSD if you can help it, **and wont support discard anyway**

Rubbish, the code for "Discard" has been in the kernel for Swap partition processing for a while now. It is always used and is not a user option.

---

### Post by haqking on 2012-12-14
> **dcstar said:**
> Rubbish, the code for "Discard" has been in the kernel for Swap partition processing for a while now. It is always used and is not a user option.

Interesting.

However it appears on the arch and debian wiki that it is a user option however ?

That being said Swap shouldnt be on a SSD where possible though which was my point, as for swap not being able to use it, i wasn't aware it could but it would appear that the user can define it.

---

