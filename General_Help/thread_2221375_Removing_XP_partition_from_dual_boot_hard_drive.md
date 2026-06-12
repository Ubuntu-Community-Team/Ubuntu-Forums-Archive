---
title: "Removing XP partition from dual boot hard drive"
date: 2014-05-01
forum: General Help
---

### Post by cscj01 on 2014-05-01
I currently have a dual boot configuration on my boot drive.  The first partition on the disk is an XP partition.  The second is my Ubuntu 12.04 partition.  The third is my swap file.

I am going to delete the XP partition and extend my Ubuntu partition (ext4) to use the space created by the delete.  When I use Gparted to look at my boot drive, the XP partition has the boot flag. while the Ubuntu partition does not.  So what steps should I take in what order so that I will have a bootable drive after I have removed XP and expanded Ubuntu?

---

### Post by SuperFreak on 2014-05-01
No idea if this would work but there is [http://ubuntuforums.org/showthread.php?t=1769489]("http://ubuntuforums.org/showthread.php?t=1769489")


Also if XP is in partition to left of Ubuntu Partition in Gparted you may not be able to expand into the old XP Partition(may be wrong here but I think you can only expand to the right). Sometimes a clean install is best option.

---

### Post by cscj01 on 2014-05-01
> **SuperFreak said:**
> No idea if this would work but there is [http://ubuntuforums.org/showthread.php?t=1769489]("http://ubuntuforums.org/showthread.php?t=1769489")


Also if XP is in partition to left of Ubuntu Partition in Gparted you may not be able to expand into the old XP Partition(may be wrong here but I think you can only expand to the right). Sometimes a clean install is best option.

XP is to the left of Ubuntu.  So I need to make sure I have a bootable drive AFTER I expand Ubuntu.  I am not sure os-uninstaller allows for that.  There seem to be more steps involved, so I'm still looking for the complete solution.  Thanks for the link though.  I did install os-uninstaller, but I wasn't sure if it was current enough as well.

---

### Post by pqwoerituytrueiwoq on 2014-05-01
you can't expand to the left, you can move to the left then expand to the right
i think ubuntu will still boot after doing that
you can format the xp partition and use it for storage by mounting it has say /home/cscj01/Videos

moving a partation has a lot of risk and is time consuming

---

### Post by pfeiffep on 2014-05-01
I agree with pqwoerituytrueiwoq - moving partitions is not for the faint of heart. 

If all you want is more space for Ubuntu  you might find this an interesting [read]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by cscj01 on 2014-05-03
Okay, I have considered the advice given here and have a proposed solution.  I also have a couple of questions associated with the solution, so I'll list them after I outline my proposed approach.

[LIST=1]
[*]Use Clonzilla to backup my Ubuntu partition.
[*]Use Gparted to delete my XP and Ubuntu partitions.
[*]Create my empty Ubuntu partition.
[*]Restore my backup of my Ubuntu partition.
[*]Expand my Ubuntu partition to the right.
[/LIST]
My questions are:

[LIST=1]
[*]Do I need to set the boot flag on my Ubuntu partition before I do the backup?
[*]Will Clonzilla restore the Ubuntu partition beginning with the first available space?
[*]
[/LIST]

---

### Post by pfeiffep on 2014-05-03
@cscj01 I have no answer to either of your questions... hopefully someone with direct Clonezilla experience will offer answers.
IMO this seems a bit complicated, perhaps you have an unstated reason to move root partition. 
With my limited knowledge of your situation I think I'd use gparted to format the XP partition to ext 4 and use the new space as you see fit.

---

### Post by monkeybrain20122 on 2014-05-03
Don't know about clonezilla, but fsarchiver is really simple to use and more flexible than clonzilla because you only clone the partition as oppose to the drive and you can restore to anywhere as long as the destination is big enough to hold the content of the partition. Clonezilla requires the targeted partition to be at least as big as the original.

 Basically clone your Ubuntu, repartition your drive and then restore the clone, no need to mess with uuid or anything. But you need a live usb with fsarchiver to restore your clone (a live usb for ubuntu will do, just install fsarchiver) and a temporary device, like an external hard drive to hold your clone. 

so let's say you have these. These are the complete instructions.
1) To make the clone
Boot into Ubuntu, install fsarchiver
```
sudo apt-get install fsarchiver
```
Find out the device name for your ubuntu partition, run the following and note the output
```
sudo blkid
```
say Ubuntu is in /dev/sda2. 
Now attach your external drive where you want to keep your clone. Let's say you want to save the clone in a folder called bak. Now open the file manager and go to bak, note the name of the drive, you should see something like /media/username/drivename/bak
Run fsarchiver
```
sudo fsarchiver -v -j2 -a -A savefs /media/username/drivename/bak/ubu.fsa /dev/sda2
```

The options -a and -A allow you do clone partitions currently mounted and in use (since you are in Ubuntu, the very partition you want to clone). You can continue to use Ubuntu during live cloning, just don't install/update/remove software or sync with dropbox etc : i.e do anything that would change system configuration. Browsing web, reading, making documents etc are fine.

 -j specifies now many threads to use, omit it if you have only one thread, or if you have 4 you can change to -j4 etc.

-v means verbose

ubu.fsa is the name of the backup file/clone. You can call it anything as long as the extension is .fsa.

2) use gparted to repartition your drive

3) restore
boot to a live Ubuntu usb, or a rescue cd with fsarchiver [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)
In ubuntu live usb needs to install fsarchiver (it is in universe)

Now attach the external device that holds the clone, again open with file manager and note the drive name ( path to drive is /media/.., like in the first part.)
Let's say you want to restore the clone to /dev/sda1
run fsarchiver
```
sudo fsarchiver -v -j2 restfs /path/to/drive/ubu.fsa id=0,dest=/dev/sda1
```

Wait til it is done and reboot, that's it (make sure you remove the live usb and the external device of course)

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)


Edited: fixed errors regarding path to .fsa file  in instructions.

---

### Post by cscj01 on 2014-05-03
Still no mention of setting the boot flag on my Ubuntu partition.

---

### Post by monkeybrain20122 on 2014-05-04
If grub is not present in your Ubuntu partition, then just install it. After restoring Ubuntu from the clone, instead of rebooting, run in the live usb (assuming ubuntu is restored to /dev/sda1)
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note that it is sda1 (partition) in the first and sda (drive) in the second.

Now reboot.

---

### Post by cscj01 on 2014-07-22
> **cscj01 said:**
> Okay, I have considered the advice given here and have a proposed solution.  I also have a couple of questions associated with the solution, so I'll list them after I outline my proposed approach.

[LIST=1]
[*]Use Clonzilla to backup my Ubuntu partition.
[*]Use Gparted to delete my XP and Ubuntu partitions.
[*]Create my empty Ubuntu partition.
[*]Restore my backup of my Ubuntu partition.
[*]Expand my Ubuntu partition to the right.
[/LIST]
My questions are:

[LIST=1]
[*]Do I need to set the boot flag on my Ubuntu partition before I do the backup?
[*]Will Clonzilla restore the Ubuntu partition beginning with the first available space?
[*]
[/LIST]

I should have marked this as Solved some time ago.  I followed the above, and everything worked great.  I need not have worried about the boot flag.

---

