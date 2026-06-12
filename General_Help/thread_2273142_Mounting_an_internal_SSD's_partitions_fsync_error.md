---
title: "Mounting an internal SSD's partitions: fsync error"
date: 2015-04-10
forum: General Help
---

### Post by flyingeagle413-f on 2015-04-10
Hello,

I have been running Xubuntu off of an external SSD on my ultrabook for the past month with no problems. My internal SSD has Windows 7 on it (NTFS partition with some other Intel rapid start stuff), and I have NEVER been able to mount the partitions on it, or for that matter, even look at them in GParted. 

When I try to mount the drive, it says the following: 
> mount: /dev/sda: can't read superblock

When I try to open up GParted with it, GParted says the following:
> Error fsyncing/closing /dev/sda: Input/output error

With some googling I found that many people with the same problem actually had corrupted partitions...
I can assure you that the partition on my internal SSD is not corrupt (in fact I just used it an hour ago).

Any attempt at an fsck tells me:
> fsck.ntfs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda
Could this be a zero-length partition?

Anyone have any ideas how I could get this to mount?
I have been dealing with this problem by simply switching to Windows whenever I need files from that drive...

(My computer has UEFI, and I boot in "insecure mode" in Xubuntu, could that be part of it)

I really have no clue what to do, any help is appreciated.

---

### Post by oldfred on 2015-04-10
Is Windows 7 in UEFI or BIOS boot mode. 
And is it Intel SRT or similar? That uses RAID or is seen as RAID from Ubuntu.
        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

    
Post this to see what is seen or not:
sudo parted -l

---

### Post by flyingeagle413-f on 2015-05-31
I figured out what it was...
I had a password set on my internal SSD when I thought it was on the computer itself. Removing that fixed it, thank you though!

---

