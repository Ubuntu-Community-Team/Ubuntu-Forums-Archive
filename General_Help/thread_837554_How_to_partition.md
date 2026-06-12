---
title: "How to partition"
date: 2008-06-22
forum: General Help
---

### Post by ProgenitorVirus on 2008-06-22
Newbie to Linux, so can somebody help me out?

I have a 500 GB HDD.  My "Main" partition where everything is stored (Equivalent to C: on Windows) has 460 GBs free.  I want to take 120 of those GBs, and partition it, and then install Windows XP on it.

I feel comfortable with the installation, but I can't seem to find out how I can make a 120 GB partition separate of the 460.

I guess, what I'm looking to do is to resize my main partition, taking away 120, which will be left as unused space until I can install Windows.

Thanks for all of your help!!

---

### Post by windoze87 on 2008-06-22
open a terminal and type ```
sudo apt-get install gparted
```, that's the GNOME Partition Editor, and should do what you're looking for.

---

### Post by ProgenitorVirus on 2008-06-22
Ok, thanks!  I have that, tried to start it, error, so sudo gparted worked.  As it loaded, I got the following error, (Could be normal?)

Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Input/output error during read on /dev/fd0

In gparted, I've tried to click the main drive

Partition   :  /dev/sda1
File System : ext3
Mountpoint  : /
Size        : 460.00 GB
Used        : 6.92 GB
Unused      : 453.08 GB
Flags       : Boot

Now from here, I'm lost.  I click it, but the resize/move button is grey, not allowing me to do anything :(

Can anybody help me get from there?

---

### Post by kdcoetzee on 2008-06-22
Get the LiveCD of gparted.

[gparted]("http://gparted.sourceforge.net/livecd.php")

I am not shore if you can just change your main hdd with gparted while that hdd is mounted.

---

### Post by windoze87 on 2008-06-22
I checked to see if i could do what you're proposing on my main HDD, and i see what you mean. Juggernaut is right, though, you can't resize a partition while it's mounted. I suggest doing what he said and getting the liveCD of gparted, while i don't have it, it may work. And yes, you must always run gparted as root :P Also, your /dev/fd0 drive looks like the permission on it is root-only, do you know what drive that is?

---

### Post by ProgenitorVirus on 2008-06-22
:p Nope, no clue what it is.

I'm a Windows user, migrating to Ubuntu, (Linux Hopeful... But also Linux newbie :P) but I have some important work-related apps I need with Windows.

Anyways, thanks for all of the help!

I'll download the liveCD right away!

Thanks!

---

### Post by cariboo on 2008-06-22
That error message about fd0 is just legacy code as most new computers no longer have a floppy drive.

Jim

---

