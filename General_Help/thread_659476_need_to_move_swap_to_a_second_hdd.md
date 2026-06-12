---
title: "need to move swap to a second hdd"
date: 2008-01-05
forum: General Help
---

### Post by onesojourner on 2008-01-05
I need to move my swap partition from 
/dev/sdb5

to 

my second hdd at sdaX. then the rest of the drive will be used for storage. Will ubuntu run alright with no swap? I have two gigs of ram right now.

---

### Post by taurus on 2008-01-05
Yes, Gutsy should run fine with no swap.  If you want to create a new swap partition, just unmount the drive and use gparted (System -> Admjnistration and if you don't have it, install it) to create a new partition and format it as Linux swap.  Then, you just need to modify your /etc/fstab to point the entry for the swap to the new partition or just add one in if you have already removed that entry in there.

---

### Post by onesojourner on 2008-01-06
ok I think I have it figured out but there is a long code with the swap loocation in the fstab. can I change the location of th swap partition and leave that as it is?

# /dev/sda5
UUID=66f45ef6-a647-4ff5-9d46-06376694dbd6 none            swap

to-------------------

# /dev/sdb1
UUID=66f45ef6-a647-4ff5-9d46-06376694dbd6 none            swap

---

### Post by cotcot on 2008-01-06
You mean the UUID ?
You can replace UUID by /dev/sdbx whereas x is the new swap partition.

---

### Post by Steve1961 on 2008-01-06
That long number is the UUID of the original swap partition.  To find the UUID of the new partition use this command in a terminal:

ls -lF /dev/disk/by-uuid/

Make sure the new UUID goes in fstab.

---

### Post by dcstar on 2008-01-07
> **Steve1961 said:**
> 
...........
Make sure the new UUID goes in fstab.

Don't bother, using UUID is basically a total waste of time for 99.99% of all Linux users (the phrase "Techno-w**k" is probably a good description for using these things on a User based distro).

Unless you are in the habit of changing the physical configuration of your internal hard drives, there is little (or no) benefit of mounting your drives using UUID.

In reference to the original post, in the "Olden days" when Linux/Unix systems had little RAM and used swap space a lot, having the swap on a separate drive improved performance considerably. These days you'd hardly notice the difference unless your hardware was under-provisioned with RAM.

---

### Post by Mike'sHardLinux on 2008-01-07
I have 3 internal hard drives on my main desktop, and before I used UUIDs in my fstab, they would always come up differently. This was a problem for me because I was mounting them in specific directories, and so sometimes the "devel" drive would be mounted under the "download" drive's folder.

I finally mounted them by their UUIDs and now everything is perfect. I don't think it is unusual for people to have multiple internal drives on their desktops.

I had thought that UUIDs were the wave of the future (and present)?

---

### Post by Steve1961 on 2008-01-07
> I have 3 internal hard drives on my main desktop, and before I used UUIDs in my fstab, they would always come up differently. This was a problem for me because I was mounting them in specific directories, and so sometimes the "devel" drive would be mounted under the "download" drive's folder.

Same here, and this is why UUIDs can be useful.

---

