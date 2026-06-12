---
title: "Can Ubuntu mount Windows XP Dynamic Drives?"
date: 2005-03-18
forum: General Help
---

### Post by fritzk3 on 2005-03-18
Hey all,

I was setting up Windows XP (upgrading from Windows 2000) and made the mistake of setting up dynamic drives/volumes instead of leaving them as basic drives.

Can Ubuntu mount these drives?  I really need to get at some of the data on these four other partitions, and I fear that Ubuntu may be my only hope.  I *think* the dynamic drive format means that the drives are using NTFS filesystem, but I'm not sure.

If I try to mount these partitions under Ubuntu, and designate an incorrect filesystem (ex. vfat), do I risk damaging the data on the other partitions?

Thanks in advance for the help...

---

### Post by TheCondor on 2005-03-18
I think its possible to do that. If I remember correctly, my drives were set as dynamic volumes under windows xp and I had no problems mounting and using them normally. I havent done this in Ubuntu though, I was using Suse back then, but I dont see a reason why it wouldnt work in Ubuntu as well. 

An answer from a more experienced user would be more helpful though, as Im relatively new to Linux  :wink:

---

### Post by fritzk3 on 2005-03-18
I'm hoping you're right.  I really hosed things by going to a dynamic drive system.  If I can get to the drives through Ubuntu, it's time to copy the critical stuff, throw it on some CDs, and then start over by FDISKing all of my Windows partitions and installing XP fresh.

---

### Post by alastair on 2005-03-18
You need the kernel to support "LDM" partitions i.e. logical disk management aka "dynamic".

ON my hoary machine (kernel 2.6.10-4), you can find the kernel config in /boot.

A look at this :

# Partition Types
#
....
CONFIG_LDM_PARTITION=y
...

So, you should be set.

---

### Post by exc220 on 2007-01-22
> **fritzk3 said:**
> Hey all,

I was setting up Windows XP (upgrading from Windows 2000) and made the mistake of setting up dynamic drives/volumes instead of leaving them as basic drives.

Can Ubuntu mount these drives?  I really need to get at some of the data on these four other partitions, and I fear that Ubuntu may be my only hope.  I *think* the dynamic drive format means that the drives are using NTFS filesystem, but I'm not sure.

If I try to mount these partitions under Ubuntu, and designate an incorrect filesystem (ex. vfat), do I risk damaging the data on the other partitions?

Thanks in advance for the help...

Hi fritzk3!
Did you resolve this issue? Did alastair's solution solve the problem?
I am very interested bc I have a windoze dynamic disk partition also!!
Thanx!

---

### Post by exc220 on 2007-02-05
any news on this issue?

---

### Post by frootloop on 2008-04-23
I'm looking for a solution to this myself! I need to mount a windows dynamic drive that is spanned accross multiple physical drives - does anyone have any ideas? I'm attempting this under Gutsy btw

---

### Post by frootloop on 2008-04-23
Finally figured it out!! Going to try later tonight, will post back if successful

---

### Post by c_monoro on 2008-05-14
and? ... anyone made it?

---

### Post by Smurph on 2008-06-09
I've been trying to mount a windows spanned volume also.  I'm a linux newbie, trying to migrate from windows.  

I did find this:
[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

Not sure if its on the right track.  Couldn't get it to work myself.

If anyone has had any luck or ideas please post!  Hoping I don't have to go buy a drive to backup my 500gb volume.

---

### Post by Smurph on 2008-06-09
Success!!

I manged to mount a windows ntfs volume spanned over two disks!  I'm running ubuntu hardy.

I followed the guide at:
[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

Particularly the section titled "The Device-Mapper driver"

Some important notes though (problems I had and how I solved them)

- Before you can use dmsetup you need to do this:

    $ sudo modprobe dm_mod

Otherwise you get a compatibility error, which should be a permission error.  The wrong error is displayed because of a bug.

- The command:

    $ sudo mount -t ntfs -o ro /dev/device-mapper/myvolume1 /mnt/myvol1

Returned an error, not found. I found it needed to be:

    $ sudo mount -t ntfs -o ro /dev/mapper/myvolume1 /mnt/myvol1

It may be different for you.

I'm a linux newbie but thats what I did and it seemed to work.  Hope it helps!

---

