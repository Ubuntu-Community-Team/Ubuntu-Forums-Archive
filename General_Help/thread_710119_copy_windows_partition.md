---
title: "copy windows partition"
date: 2008-02-28
forum: General Help
---

### Post by zxscooby on 2008-02-28
I bought a new laptop with vista installed and also a larger hard drive.
I swapped out the drives and installed kubuntu.
my question is , i want to create a partition on the new drive and copy vista from the old drive to the new one. Should i just be able to update my grub configuration and have dual boot, or is it more complicated than that. i was thinking of hooking the drives up in my desktop and using DD to clone windows to the new partition. Any sugestions or advice appreciated.

---

### Post by clb137 on 2008-02-28
HI,

If you need vista and Ubuntu on the same drive the reccomend way is to have Vista installed first, then isntall Ubuntu on it, the Ubuntu inslaller can resize your partion, trying the other way round is not the way to go.

there are loads of howto's on this site on this subject

good luck if yiou need any more info just contact me

Clint

---

### Post by zxscooby on 2008-02-28
The problem is i dont have an install cd and i wanna use the bigger drive
not to mention it was a big deal to get this rig up and running due to driver issues and such.

---

### Post by az on 2008-02-28
> **zxscooby said:**
> I bought a new laptop with vista installed and also a larger hard drive.
I swapped out the drives and installed kubuntu.
my question is , i want to create a partition on the new drive and copy vista from the old drive to the new one. Should i just be able to update my grub configuration and have dual boot, or is it more complicated than that. i was thinking of hooking the drives up in my desktop and using DD to clone windows to the new partition. Any sugestions or advice appreciated.

It's simple to copy a partition from one drive to another.  Just use the live cd to do it.  Plug your source drive into your computer using an external usb enclosure (or something) and run (G)parted on the internal (big) drive.

Shrink and move the Kubuntu partition to the end of the drive.  Create enough free space to fit the Vista partition from the other drive.  Create an windows NTFS partition as the first partition on the disk.

copy the partition from the source drive to the new one.  You can use parted from the command line to do that.  
[I]cp [source-device] source dest
    copies the source partition's filesystem on source-device (or the current device if no other device was specified) to the dest partition on the current device.[/I]

so to copy the first partition from sdb to the first partition of sbd, it would be
cp /dev/sdb 1 1

Next, you need to reinstall grub, add windows to the grub menu.list and you should be good to go.

---

### Post by zxscooby on 2008-02-28
Thanks Az, 
                   That seems like a no frills way to go. Just for fun though, what if i wanted 

to put windows on the second partition? I could follow the same procedure?

---

### Post by zxscooby on 2008-02-28
bump

---

