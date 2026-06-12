---
title: "I Messed up big time and need some help..."
date: 2008-06-02
forum: General Help
---

### Post by mike_pasara on 2008-06-02
I had my computer set up in the following way

Internal Laptop Hard drive
partition 1
Windows Vista C: (40gb)

partition 2
NTFS Folder for media (173gb)

partition 3
Ubuntu (20gb)

External USB
Parition 1
(298gb)



Now here is what I did...

Needed space so I used disk management from vista. Whiped out the 20gb ubuntu partition and merged the unallocated 20gb to the C: in vista.

Not a problem, the thign is i haven't restarted my computer at that point.

Finally i restart the computer. Here is the problem. Now I'm thinking my MBR is still set up to ask which OS I want to run. It's trying to find Ubuntu but it's no longer there and just hangs. It says Error 17 or Error 18. It does not allow me to load windows.

I'm using a live CD right now and It won't let me access my external. What are my options here I have 40% of my 173gb partition that needs to be backed up and about 10 gigs of data I need from my now 60gb partition.

How can I save this data?

My external might not be able to handle all these files and is also formatted in fat32 because i hook it up to my ps3. Live CD is in my drive so I can't burn them to DVD's. The biggest thing I have for storage is a 4 gig memory stick.



Once I have all of this data saved I will then reformat the entire drive whipe it clean and start from scratch. So my cry for help is how do I save my data.

---

### Post by lisati on 2008-06-02
First of all, take a deep breath, and congratulate yourself for asking for help.

There are options available, which some of the more technically-aware users of this forum might be able to help with.

My first suggestion is to try to discover what's actually on your hard drive.

---

### Post by Rocket2DMn on 2008-06-02
If you haven't removed Vista, you can have a look here to restore the MBR to give windows control instead of GRUB which has been erased: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You will need the /fixmbr and /fixboot commands I believe.

---

### Post by mike_pasara on 2008-06-02
> **lisati said:**
> First of all, take a deep breath, and congratulate yourself for asking for help.

There are options available, which some of the more technically-aware users of this forum might be able to help with.

My first suggestion is to try to discover what's actually on your hard drive.

Ha ha. Thanks. All I want to do is backup my media partition on my drive which I can access. Along with that I want to backup My pictures and My documents from my c: drive.

I just need a way to get all that data I have access to to go onto my unaccessible external. I'm a linux noob and have no idea what I'm doing.

---

### Post by Rocket2DMn on 2008-06-02
You should be able to manually mount the hard drive partitions from the LiveCD
```
sudo fdisk -l
```
Then mount the appropriate partitions by making the mount points and running the mount command.  ex:
```
sudo mkdir /media/<mountpoint>
sudo mount -t <filesystem_type> /dev/<device> /media/<mountpoint>
```
So something like:
```
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/sda1 /media/sda1
```

---

### Post by mike_pasara on 2008-06-02
> **Rocket2DMn said:**
> If you haven't removed Vista, you can have a look here to restore the MBR to give windows control instead of GRUB which has been erased: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
You will need the /fixmbr and /fixboot commands I believe.



This worked PERFECTLY. I am now running 100%, I think I'm going to spend some time tomorrow backing up data :P

Thank you very much Rocket2DMn

---

