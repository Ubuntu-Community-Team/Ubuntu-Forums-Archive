---
title: "how do I remove windows?"
date: 2007-06-15
forum: General Help
---

### Post by Cirrocco on 2007-06-15
I would like to remove the windows partition all together from my laptop.
/sda1: (fat32) dell utils
/sda2: (ntfs) winxp
/sda3: (ext3) Ubuntu
/sda4: Extended {
     /sda5: linux-swap
     /sda6: (ext3) storage space
}

I plan to expand ubuntu's partition to give it more room by getting rid of my ntfs partition.
How can I remove sda2 completely without frigging up Ubuntu?

can I just adjust my /etc/fstab?
or does this also mess up the pointers in the /boot?

I'm prepared to just shrink sda2 down to a few megs so it doesn't take up any room worth talking about - but I'd like to do this cleanly.

---

### Post by mopey on 2007-06-15
No, you can't just modify /etc/fstab.

You need to repartition /dev/sda2.  For this, you can use something like fdisk, parted, or (possibly easiest) gparted.  First delete the Windows partition so it's free space, then resize your linux partition to take advantage of it.  Resizing partitions can be risky (might lose data) so be sure to backup important stuff before doing it.

Does that help?

---

### Post by dreadlord_chris on 2007-06-15
> **Cirrocco said:**
> I would like to remove the windows partition all together from my laptop.
/sda1: (fat32) dell utils
/sda2: (ntfs) winxp
/sda3: (ext3) Ubuntu
/sda4: Extended {
     /sda5: linux-swap
     /sda6: (ext3) storage space
}

I plan to expand ubuntu's partition to give it more room by getting rid of my ntfs partition.
How can I remove sda2 completely without frigging up Ubuntu?

can I just adjust my /etc/fstab?
or does this also mess up the pointers in the /boot?

I'm prepared to just shrink sda2 down to a few megs so it doesn't take up any room worth talking about - but I'd like to do this cleanly.

You would be better off just reformatting the partition for Ubuntu. Since you Ubuntu partition comes after your Windows partitions - it's a bit of a hassle to merge the two. By the way, what are you planning on doing with /sda1 - if you are getting rid of Windows you might as well just get rid of it too.

Anyway, I would recommend just deleting the partition(s) and creating a new one formatted ext3 - then moving your /home partition to it: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by statictonic on 2007-06-15
sudo apt-get install gparted

Good GUI partition tool, looks similar to a tool like partition magic, works great.  Should be able to do what you need.

---

### Post by Cirrocco on 2007-06-15
Thanks for the replies, people.

While I really see the advantage of just reinstalling - I'd like to avoid that until I screw up my computer on some other caper I'll likely be on in the future.

I also like some of the features of the Dell utility partition (it's linux y'know!.  And it's only 80Mb or so.

I'm sorry I forgot to mention my intentions for using gparted (live cd) to do the dirty work.
I just have the feeling that after using it to remove one partion, and resize another - my system won't boot.

In just such an event - how do I recover?  Ubuntu live cd + edit /etc/fstab?  Super Grub Disk?

---

### Post by dreadlord_chris on 2007-06-15
> **Cirrocco said:**
> Thanks for the replies, people.

While I really see the advantage of just reinstalling - I'd like to avoid that until I screw up my computer on some other caper I'll likely be on in the future.

I also like some of the features of the Dell utility partition (it's linux y'know!.  And it's only 80Mb or so.

I'm sorry I forgot to mention my intentions for using gparted (live cd) to do the dirty work.
I just have the feeling that after using it to remove one partion, and resize another - my system won't boot.

In just such an event - how do I recover?  Ubuntu live cd + edit /etc/fstab?  Super Grub Disk?

This is one reason I say you would be better off just deleting/creating a new partition and formatting for Ubuntu - this way your /dev points remain unchanged, the only editing of fstab would be to change the filesystem type of sda2 from ntfs to ext3 (or whatever you format it too). Even if you don't use it for a seperate /home partition  - you can still use it as extra storage.

As I said, it's a bit of a hassle to increase a partitions size by merging with free space that comes before it. Basically you would have to:
1. Delete the Windows partition
2. Create a new partition
3. Format it
4. Bit-copy the data from the partition you want to resize to the new partition (did I mention the new partition needs to be >= size of the partition you are 'resizing'
5. Delete the old partition you wanted to resize
6. Now that you have free space *following* a partition - you can actually, *safely* resize it.
7. You see how sticky this is gettiing? From here you're gonna have to edit your fstab - and based on your initial setup you might need to reinstall GRUB, depending on where it was initially installed. And yes, all the pointers in /boot would have to be relinked....

Sound like fun?

---

### Post by Cirrocco on 2007-06-15
> **dreadlord_chris said:**
> ...And yes, all the pointers in /boot would have to be relinked....

Sound like fun?

/boot pointers...blah, nevermind.

Thanks, guy.

reinstall FTW.

---

### Post by mopey on 2007-06-15
I think if fstab these days they use UUIDs so the /dev points don't matter.  I think you can just resize it semi-safely without even having to edit it (I could be wrong).

Anyway, worst case scenario, you could try it, screw up, and reinstall anyway.  So I would at least give it a try.

---

