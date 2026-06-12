---
title: "Recover software RAID 1"
date: 2007-08-12
forum: General Help
---

### Post by etamax on 2007-08-12
Hi to all!
I need a big help from you! On my Ubuntu I had created a software RAID 1 with 2HD 300GB SATA. After various power failures the system wasn't bootable and after a series of fsck, everything seems to get worse. I started to read guides over internet and at the moment I have stopped and removed RAID with these commands:

```

mdadm --manage --stop /dev/md0
mdadm --manage --remove /dev/md0

```

I have done test over partitions, blocks, inodes, superblocks on the second HD (sdb); sda should be "intact". I have written it beetween quotations marks because I don't know if my data are there or not.
If I type

```

fsdisk -l

```

I get

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36388   292286578+  83  Linux
/dev/sda2           36389       36481      747022+   5  Extended
/dev/sda5           36389       36481      746991   82  Linux swap / Solaris

```

if I try to mount sda1 (that seems to be the partitions where I had my data)

```
mount: unknown filesystem type 'linux_raid_member'
```

If I try to re-create MD0 with these commands

```

mdadm -C /dev/md0 -l1 -n2 /dev/sda1 missing
mke2fs /dev/md0

```

and then mount it, inside the mount point I found only the folder "lost+found" that is empty.

I am doing this tests with an Ubuntu Live CD and when I install mdadm I get this message

```

update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
 * Starting MD monitoring service mdadm --monitor                        [ OK ] 
 * Assembling MD array md0...                                            [ OK ] 
 * Assembling MD array md1...                                            [fail] 
 * Generating udev events for MD arrays...                               [ OK ]



root@ubuntu:/home/ubuntu# cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sda1[0]
      292286464 blocks [2/1] [U_]
      
unused devices: <none>



root@ubuntu:/home/ubuntu# mount /dev/md0 /mnt/raid

root@ubuntu:/mnt/raid# ls -l
total 16
drwx------ 2 root root 16384 2007-08-11 18:00 lost+found

```

Why "Total 16"?



I have no other ideas and I am seriously worried about my data :'

What should I do?



PS: sorry for my bad english

---

### Post by fjgaude on 2007-08-12
We are all learning, day-by-day.

The only thing I don't understand is what happens when you did the:

```

mdadm --manage --remove /dev/md0
```

I think this remove command is for a device, not an array. You might have used /dev/sdb1 there instead. The --stop command deactivated the array and let the two drives be free. I hope the fsck didn't do bad things if you applied it to the array, /dev/md0. And what is the md1 all about?

And when you did an fdisk -l where is your other drive, /dev/sdb1 I suppose? Have you unmount it?

On the other hand, you likely erased everything when you did:

```
mdadm -C /dev/md0 -l1 -n2 /dev/sda1 missing
mke2fs /dev/md0
```

frank

---

### Post by etamax on 2007-08-12
Thanks for your answer Frank.

Yes, maybe you are true, I was a bit confused and I wrote /dev/md0 insted of /dev/sdb1.

The other drive is sdb1 but I don't think it is "intact" because I have done lots of tests and changes with the partitions and superblocks.

I realized that the mke2fs was a very bad idea...
At this point is there anything to do to recover data? They are very important for me :(

---

### Post by fjgaude on 2007-08-12
I don't have any experience with what mke2fs does to an array. In your case it might have been just to the active drive, since you have the "missing" in the array create, the mdadm -C command.

You would need a disk data recovery expert to try to get as much data back as possible. I'm not one of those folks. <sigh>

There are companies that specialize in data recovery. You might try your local telephone book, or a Google search.

Sorry I can't be of more help.

frank

---

### Post by shawncorn on 2007-11-18
Hey, I don't know if you're still having trouble, but there are a few things I know of to recover your data.

Your stuff is still there.  Formatting the drive doesn't actually overwrite it.  If you can repair the FS with some tools, I'd try that first.  Failing everything else, there's a utility I found a long time ago that scans the drive block by block looking for patterns signifying the beginning and end of certain file types.  It sort of works for .jpg files, and .pdfs.  It works well with something like html.  Etc.  It supports searching backwards and forwards and by different block sizes.  So the amount of data you recover depends on the amount of research you're willing to do with different file types and how creative you are in specifying patterns for the beginning and end of them.

Unfortunately, I can't remember what it was called. :)  It was developed by someone in the US Air Force.  I will google it and get back to you if I find it; otherwise, maybe you could write yourself a similar utility.  Good luck.

---

