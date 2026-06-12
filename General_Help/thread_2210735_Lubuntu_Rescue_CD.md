---
title: "Lubuntu Rescue CD"
date: 2014-03-12
forum: General Help
---

### Post by Chris_Lawrie on 2014-03-12
Hi

Normally with Windows I use freeware such as Macrium to create a rescue CD and snapshot of the disk once I have it how I want it so I can always get back to that state if I need to. Macrium say they do not support Lubuntu or other linux based systems so I was wandering how I go about creating a rescue CD for my Lubuntu installation once I have it on my laptop? Ideally when my drive gets a bit cluttered Id back up the data and boot up the original version again.

New to Lubuntu so there is likely an obvious answer I dont know about or something that is an add on to the basic installation that does this.

---

### Post by grahammechanical on 2014-03-12
The DVD/USB memory stick that you used to install Lubuntu on your machine will run a live session and from that you can run commands to try to fix things.

We also have a Recovery mode that we access through the boot menu Advance Options sub-menu. This gives us options to make free space; repair broken packages; check all file systems, update the boot loader, enable networking and get us a root shell prompt. With networking enabled and a root shell prompt we can not only edit system files (if we know what we are doing) but also install and remove applications and packages that may need reinstalling to fix the problem.

We can always re-install and provided that we do not format the hard disk/partition at the same time all our files and settings in the /home folder will not be affected.

Some of us a separate folder that we set for /home when we install Ubuntu and its flavours (such as Lubuntu). Then we can install and format the Ubuntu/Lubuntu partition without any risk of deleting our documents and data.

And then there is this:

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Now, there is a Rescue disk to have in reserve.

Regards.

---

### Post by Lars Noodén on 2014-03-12
If you make a separate /home partition, the re-installation will be that much easier.  During the re-install you can tell it to leave /home alone and it will not be touched.  It's still essential to back up everything anyway just in case.

---

### Post by Mark Phelps on 2014-03-12
To make a "snapshot" of the disk, you can make full image backups using either Clonezilla or RedoBackup.  The first is more powerful, but harder to use, the second is menu-based and is easier to use.

---

### Post by Chris_Lawrie on 2014-03-13
Thanks for the suggestions.

A lot of those options rely on having Lubuntu still on the PC before in order to revert back. What I require is once I have it working and the addons correct I would like a rescue CD/drive whatever that I can boot from and it will reinstall the system as it was. There may be Lubuntu still on, there may be Windows and there may be no drives at all setup. Would the RedoBackup option sound like the easiest for this purpose? I dont foresee actually having any improtant data saved in folders it will mosrly be to revert to a fresh initial copy now and again. Although I guess this will involve more and more updates as time goes by...

---

