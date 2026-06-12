---
title: "Problem with external HDD reiserfs automount default permissions."
date: 2007-10-20
forum: General Help
---

### Post by endo on 2007-10-20
Hello, I bought an external HDD, which is connected to the PC via a USB cable. So far so good.
I formatted it with vfat and it works perfectly. Then I decided to re-format it using the ReiserFS filesystem, so as to be able to copy files more than 4 GB to it (as fat32 has this limitation).
The problem is that when I formatted it to ReiserFS, I plugged it in and it automounted as expected. But when I tried to write to it, I was told I had no permissions to do it. When I checked the mount-point (automatically created by the automounter), I noticed that its permissions were drwxr-xr-x and it was root's property. So obviously, only root can write to the drive and no ordinary user.
I did another test with FAT32 and noticed that this time the automounter creates the mountpoint as expected - it is owned by the current user, not root.

But I want reiserfs, and every time I plug the drive in, formatted with the reiserfs filesystem, the mountpoint is automatically created as owned by root and only he can write to it. :(

So, how can I configure the automounter in such a way, that when I plug the ReiserFS drive in, the mount point is created with write permissions for the current user (not root)?

Or in other words: How can I change the settings that determine the ownership of the mountpoint, that is automatically created, when my external HDD is plugged in? When I plug a vfat-formatted medium, the automatically created mount point is owned by the current user (not root). I want it to be the same with ReiserFS, so that I am able to write to it.

Any ideas?
Thanks in advance. :)

---

### Post by Zillion on 2007-10-20
I have a similar problem under Kubuntu. I have an external hdd (called LACIE) formatted as NTFS, but it won't auto show up.

Now if I do

> sudo mount -t ntfs-3g /dev/sdd1 /media/LACIE -o force
 it will show under Root/media/LACIE and I can read and write without problem.

On Fstab I entered > /dev/sdd1	/media/LACIE 	ntfs-3g	defaults, force 0 

How can I accomplish it that it will show auto under " Storage Media " ?

---

### Post by Squish on 2007-10-22
I am having the same problem.

In my honest opinion, I am very unimpressed with the plug and play of this.

My wish is that I could get write permissions easily once I mount it.
I have a 750gb sata II 32mb, in a nexstar 3, and when I plug it in, it does mount, but I can only read, not write. this is with ext3, and reiserfs.

I want to use reiserfs because of the performance advantages, but if getting write permissions is going to be this much of a pain, then I will very frustrated.

I also want to be able to goto other computers and read and write, possibly also boot off this.

What is the best course of action?

---

### Post by Chriswaterguy on 2007-11-19
I have the same problem with an ext3 USB-HDD. 

I use 
> gksudo nautilus
and navigate through /media to find the HDD. This is annoying for me, and would be an even bigger headache for a complete newbie. 

Being forced to use root priveleges when they shouldn't be necessary looks to me like a security flaw. A newbie doing this could conceivably get mixed up and change system files. Especially if they leave nautilus open with root priveleges, and later use that instance of nautilus for something else. (In Thunar, i.e. Xubuntu, at least the file manager with root priveleges is marked in red; in Gnome it looks the same, apart from some different settings in the sidebar on the left.)

---

