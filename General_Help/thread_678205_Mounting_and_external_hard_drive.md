---
title: "Mounting and external hard drive"
date: 2008-01-25
forum: General Help
---

### Post by vnetha on 2008-01-25
Hi,

I have Gutsy installed on my old DELL Optiplex GX280.
And I'm trying to use a Seagate FreeAgent hard drive (500 gigs) on it.

The system usually doesn't recognize the drive when I plug it in.
So I do an...

```
sudo fdisk -l
```

followed by...

```
pmount /dev/sdb1
```

It works fine as long as I'm continuously using it.
meaning, playing movies or music or actively transferring files.
But if I leave it alone for (lets say) 5 minutes, it somehow automatically unmounts itself.

then I have to unplug it, replug it and go through the whole deal again.

I'm looking for a solution where the system will **automatically mount** the hard drive, 
every time it is connected and **stay connected**.

funny thing is, it does detect the drive sometimes, but doesn't do so always.
i have no clue why.

Please help!


Vivek.

---

### Post by Rocket2DMn on 2008-01-25
By default, you can't prevent it from unmounting, it's the stupid FreeAgent firmware on the drive that has it go into some sort of low power or standby state when it's not being used.  It works fine in windows, but seagate has basically given linux users the proverbial finger on this one by not making it very compatible.
As far as I know, the best way to keep the drive alive and mounted is to have a script that does some sort of access to the drive on a regular basis.  See this thread - [http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673)
Some users there managed to get it to stay mounted under Feisty, and I think eventually under Gutsy as well.

---

### Post by rosegarden78 on 2008-01-25
If it's mountable it should be in /etc/fstab note the contents with nano then plug in device run nano /etc/fstab and look for Johnny-Come-Lately may also have to check /etc/mtab mount using this command

sudo mkdir /mnt/temp
sudo mount /dev/sdb1 /mnt/temp

---

