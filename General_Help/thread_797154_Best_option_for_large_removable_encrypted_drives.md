---
title: "Best option for large removable encrypted drives?"
date: 2008-05-17
forum: General Help
---

### Post by musther on 2008-05-17
I've recently moved my desktop to a fully encrypted system (encrypted LVM).  On here I have all of my personally created data, basically stuff I can't afford to loose, photos for example.  This is backed up weekly.

Now for my large data storage, media etc, I don't do backups, because it can be replaced if lost, stolen or damaged - not easily, but it can.  For this data, I use large external hard drives.

I would like to encrypt this large external storage, but I'm not sure what's the best tool for the job.  I'm very familiar with encfs, and I'm quite familiar with TrueCrypt, so those are the two I'm looking at.

I must admit, I like encfs, but would really rather a single container than a pass-through filesystem, but my main concern is data stability.

If I use truecrypt, and let's say I create a 250gb container on one of my external drives, and create an ext3 (or whatever else) filesystem in there, my worry is filesystem degradation.  Basically, will this truecrypt volume contained filesystem every be checked by fsck?  Is this a flaw or major problem with encrypted volumes?

So, all advice and suggestions are welcome...  Fire away :-)

---

### Post by storm99999 on 2008-05-17
According to the Truecrypt Faq ([here]("http://www.truecrypt.org/faq.php")), it states that the mode of encryption allows one sector to die and it won't trash the system, but only the local 128 bit block.

> In encrypted data, one corrupted bit usually corrupts the whole ciphertext block in which it occurred. The ciphertext block size used by TrueCrypt is 16 bytes (i.e., 128 bits). The mode of operation used by TrueCrypt ensures that if data corruption occurs within a block, the remaining blocks are not affected.

And additionally, if you frequently back up, you can fdisk it yourself if you feel so inclined, possibly even script it, but it may not much be necessary.

If I was sufficiently paranoid, I would have two separate containers (maybe with ext3 on one, xfs or something on another, just in case...) so that I am only writing to one at a time so if one dies, the other doesn't, and if a sector fails, the other partition should work.  A full drive failure would be recovered from the desktop.  I'd back up the encryption header to a USB key elsewhere, so if the corruption is in the first 1024 bytes, there's still a backup.

However, my levels of protection would depend on just how valuable the data is to me.

---

