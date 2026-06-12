---
title: "Overwrote partitions with an install: is data recovery available?"
date: 2013-01-04
forum: General Help
---

### Post by llano on 2013-01-04
**_Opening_**
I'll start with the standard, "I should have made a backup."  I didn't.  I'm pissed.  I ordered 2 hard-drives to prevent what I'm about to describe from happening in the future.

**_The Situation_**
I was bored playing on my computer today so I decided to upgrade my backup OS, from Ubuntu 10.10, to LUbunutu 12.10.  My primary OS is Arch Linux.  I was lazy during the install and decided to trust the LUbuntu installation with the "Delete existing Ubuntu 10.10, and replace with Lubuntu" option, instead of using the "Do something else installation (where I could have picked the partition setup".  My thought was, that the "delete existing Ubuntu" would only have touched the Ubuntu partition.  That turned out to be an incorrect assumption. The LUbuntu installation proceeded to wipe my entire partition setup and create a new 2 partition setup, taking out my primary OS and my Home drive. OMG TERROR!

I'm a bit distraught here as you can imagine. I'm most concerned about resumes, photo's, music, videos, and all my setups, ssh keys, and gpg encrypted passwords to every online service I use.

**Some Details**
The previous setup was as follows for my 500 gb hard drive:
/dev/sda1  P  Arch-Linux   ~20GB
/dev/sda2  P  Ubuntu 10.10 ~10GB
/dev/sda3  P  Home         ~465GB (less the bits to bytes difference)
/dev/sda4  S  Swap         ~4GB

The current structure is 2 partitions.  I'm running from a Live-USB at the moment to stay off the hard drive as much as possible. 

**What I've Tried**
* Basic Testdisk / PhotoRec run
Testdisk sees the old Ubuntu 10.0 partition and a portion of the Home partition, but states it is unable to read any files due to a damaged or corrupted filesystem.
PhotoRec only finds data relating to the new partitions (LUbuntu)

**Are there other options?**
What other options are available to me?
Are there some advanced settings in TestDisk that I'm missing which may help identify the original partition structure?
Are there ways to recover files even after the partition structures have been overwritten.

Everything I seem to read is either about recovering deleted files from a known partition, or recovering partition tables that have been messed up, but where no data has been written.  I know my primary OS is screwed because LUbuntu would have been written over the beginning of the disk, but I'm hoping there is a way to recover my later Home partition which was on /dev/sda4.

Anything anyone can do to help would be appreciated.

Thanks
-Dave (llano)

---

### Post by zvacet on 2013-01-05
Did you tried Deeper search with Testsidk? See [here.]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

---

