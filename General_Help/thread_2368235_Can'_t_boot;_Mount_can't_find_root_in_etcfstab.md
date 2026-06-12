---
title: "Can' t boot; Mount: can't find /root in /etc/fstab"
date: 2017-08-08
forum: General Help
---

### Post by tomheslinga on 2017-08-08
Suddenly got this error while booting in 16.04 and couldn't find any post with the same problem. The only thing I can think of having done wrong was unlocking my disk from the launcher.
Checked the file system in Gparted. No errors.

Here' s my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=dd19b061-c50e-4b61-a0e3-c2432441b11d /               btrfs   defaults,subvol=@ 0       1
# /home was on /dev/sda3 during installation
UUID=dd19b061-c50e-4b61-a0e3-c2432441b11d /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda4 during installation
UUID=5d4e0fa5-784a-4b6e-8972-0ebfa015369b none            swap    sw              0       0
```

---

### Post by yancek on 2017-08-08
You fstab clearly shows the / (root) partition on sda3.  Not sure why there is an entry for /home when it is on the same partition as /.

> # / was on /dev/sda3 during installation
UUID=dd19b061-c50e-4b61-a0e3-c2432441b11d /               btrfs   defaults,subvol=@ 0       1

---

### Post by Bashing-om on 2017-08-08
tomheslinga; Hello; My Welcome to the forum.

In addition :
> 
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= ..............

I do suggest that these UUID's of the fstab file be verified; 
```

sudo blkid -c /dev/null -o list

```
(clears the cache and get new view)

problem resolution

[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by oldos2er on 2017-08-08
Thread moved to General Help.

---

### Post by tomheslinga on 2017-08-08
Thanks. UUID is the same..
Running from live-usb

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /rofs          
/dev/sda1  ntfs    Door systeem gereserveerd (not mounted) A67CC80D7CC7D5E9
/dev/sda2  ntfs             /media/ubuntu/9C82F4EA82F4C9B2 9C82F4EA82F4C9B2
/dev/sda3  btrfs            (in use)       dd19b061-c50e-4b61-a0e3-c2432441b11d
/dev/sda4  swap             [SWAP]         5d4e0fa5-784a-4b6e-8972-0ebfa015369b
/dev/sdf1  ntfs    Hitachi  /media/ubuntu/Hitachi 1A31001930FFF999
/dev/sdg1  vfat             /cdrom         CACB-CDF6
```

---

### Post by Bashing-om on 2017-08-08
tomheslinga; Well ...

As pointed out by yancek; you can not mount 2 partitions to the same UUID/
You have / and /home with the same UUID .
The blkid output does not show a /home .

Not a clue as to how :
> 
# / was on /dev/sda3 during installation
# /home was on /dev/sda3 during installation

such can possibly happen without some form of user intervention.

[INDENT][INDENT]2 places at once
[INDENT][INDENT]uh uh
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tomheslinga on 2017-08-09
Thanks for helping. Not sure I understand.. /home is just a folder right?
Tried removing the entry for /home in fstab. Same problem.

```
 # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=dd19b061-c50e-4b61-a0e3-c2432441b11d /               btrfs   defaults,subvol=@ 0       1
# swap was on /dev/sda4 during installation
UUID=5d4e0fa5-784a-4b6e-8972-0ebfa015369b none            swap    sw              0       0
```

---

### Post by yancek on 2017-08-09
> Not sure I understand.. /home is just a folder right?

Yes but you had a separate entry for home as if it were on a separate partition in your fstab.  You can create a separate /home partition and many people do this.  If you commented out or deleted the fstab entry for /home and re-booted and still get the error I'm not sure what the problem is.

---

### Post by tomheslinga on 2017-08-09
To compare, I had a look at fstab from my office PC, also 16.04, which boots fine. It's basically the same..

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=4116a9fa-113e-45e8-acdd-2cc5756dbabe /               btrfs   defaults,subvol=@ 0       1
# /home was on /dev/sda1 during installation
UUID=4116a9fa-113e-45e8-acdd-2cc5756dbabe /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda5 during installation
UUID=7f2077cc-f280-4ad9-94a9-423e6e28b38e none            swap    sw              0       0
```

---

### Post by oldfred on 2017-08-09
I do not know btrfs, but it looks like it allows sub-volumes. And your fstab seems to be using that.
So mount to same UUID may be valid, but do not know if Ubuntu supports that or not?

[https://btrfs.wiki.kernel.org/index.php/SysadminGuide#When_To_Make_Subvolumes](https://btrfs.wiki.kernel.org/index.php/SysadminGuide#When_To_Make_Subvolumes)

For average user ext4 is generally better. And some of the advanced features of btrfs may not yet be totally stable.
 Redhat depreciating btrfs
[http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project](http://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project)
Linux 4.11 File-System Tests: EXT4, F2FS, XFS & Btrfs
[http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux-411-fs&num=1)

---

### Post by tomheslinga on 2017-08-10
> **oldfred said:**
> I do not know btrfs, but it looks like it allows sub-volumes. And your fstab seems to be using that.
So mount to same UUID may be valid, but do not know if Ubuntu supports that or not?


I don' t know if it's a subvolume, but this is the way the ubuntu installer installed it. It worked well for over a year, and is still working fine on my other pc, so maybe like you say the problem is it's not stable.. somehow something must have changed now that it's not working :confused:

---

### Post by oldfred on 2017-08-10
If that is how it installed, then obviously Ubuntu does work with sub-volumes.

If you had ext4 I would suggest running fsck, but fsck is only for the ext2, ext3, & ext4 family of formats. I assume btrfs has a similar file check program. 
So find & run that.

---

### Post by tomheslinga on 2017-08-10
> **oldfred said:**
>  If you had ext4 I would suggest running fsck, but fsck is only for the ext2, ext3, & ext4 family of formats. I assume btrfs has a similar file check program. 
So find & run that.
Thanks
Yeah, I did a check with the latest version of Gparted. No errors. Seems like I'm running out of options

---

### Post by oldfred on 2017-08-10
Gparted may not be reporting internal errors that a full file check program would.
I would still run a btrfs file check.

---

### Post by tomheslinga on 2017-08-11
> **oldfred said:**
> Gparted may not be reporting internal errors that a full file check program would.
I would still run a btrfs file check.

Thanks for the tip. Ran btrfs check. No errors

```
tom@tom-System-Product-Name:~$  sudo btrfs check /dev/sda3
Checking filesystem on /dev/sda3
UUID: dd19b061-c50e-4b61-a0e3-c2432441b11d
checking extents
checking free space cache
checking fs roots
checking csums
checking root refs
found 28119941171 bytes used err is 0
total csum bytes: 26764552
total tree bytes: 591118336
total fs tree bytes: 507576320
total extent tree bytes: 43040768
btree space waste bytes: 133513239
file data blocks allocated: 41058029568
 referenced 27114491904
tom@tom-System-Product-Name:~$ 

```

---

### Post by #&amp;thj^% on 2017-08-11
Have you tried yet with the repair flag?
```
sudo btrfs check --repair /dev/sda3
```
It might show more to help us here.

---

### Post by tomheslinga on 2017-08-11
```
ubuntu@ubuntu:~$ sudo btrfs check --repair /dev/sda3
enabling repair mode
Checking filesystem on /dev/sda3
UUID: dd19b061-c50e-4b61-a0e3-c2432441b11d
checking extents
Fixed 0 roots.
checking free space cache
cache and super generation don't match, space cache will be invalidated
checking fs roots
checking csums
checking root refs
found 28119941171 bytes used err is 0
total csum bytes: 26764552
total tree bytes: 591118336
total fs tree bytes: 507576320
total extent tree bytes: 43040768
btree space waste bytes: 133513239
file data blocks allocated: 41058029568
 referenced 27114491904
ubuntu@ubuntu:~$ 
```

Still not booting. Maybe I should mention some more of the errors while  booting. 

```
Mount: mounting /dev on /root/dev failed: no such file or  directory
```

---

### Post by SeijiSensei on 2017-08-11
I don't understand the reference to /root at all.  That's just the root user's home directory under the "root" of the filesystem /.

Are you sure there is a /root directory?  Maybe you just need to create it
```
sudo mkdir -p /root; sudo chown 700 /root
```

I know nothing about btrfs.  If you are mounting the same filesystem to both / and /home, where is /root (or anything else like /var) located?  Maybe the OS is looking for /root under /home rather than under /?  Is it possible to create another one of those "subvolumes" for /root in /etc/fstab?

Is there some reason that you need to use btrfs?  Can you backup up your files and reinstall with ext4?

---

### Post by tomheslinga on 2017-08-11
Thanks. I hope I understand correctly.  There is a root folder. Running from usb live-system, this is the listed location; /media/ubuntu/dd19b061-c50e-4b61-a0e3-c2432441b11d/@ I'm just not able to access it because of limited permissions. The other system folders like VAR are there to. 
Home folder is at: /media/ubuntu/dd19b061-c50e-4b61-a0e3-c2432441b11d. So basically on my Ubuntu-partition it lists two folders; @ and @home.
I have no idea why the system isn't finding root...

I'm using btrfs because I thought it would be best at dealing with corruption on a ssd, something that seems to happen more often on my ssd's.

It is beginning to look like reinstalling will be the only choice.

---

### Post by #&amp;thj^% on 2017-08-11
Very sorry to hear this! :(
Best advice I can offer is not to use btrfs without a robust backup scheme. (And apologies this is like offering a glass of water to a drowning person. )
If you are patient I'm some what confident someone might be able to help still...but that's your call.
Good Old EXT4 all the way here.

---

### Post by The Cog on 2017-08-11
I have used btrfs to boot from. In summary, yes btrfs allows the use of subvolumes in the same btrfs partition. You can mount a btrfs partition manually from linux and unless you specify a subvolume or the default has been changed, this mounts the root as it would with (say) an ext partition. The subvolumes look like folders inside the root partition to "ls" but they are created with a "btrfs subvolume create" command rather than a normal folder created with "mkdir". By default the linux installer will create subvolumes @ and @home and they get mounted at / and /home respectively. So if you mount the root volume you will see folders like:
@    (actually a subvolume, gets mounted as /)
@/bin
@/boot
@/etc
@/home   (mount point for subvolume @home)
@/root
@/sys
... and others...
@home    (actually a subvolume, gets mounted at /home)
@home/user1
@home/user2
etc.

You can use "mv" to rename subvolumes but that will break entries in fstab that use subvolume names (e.g. "subvol=@"). You can of course use "btrfs subvolume create snapshot ..." to create snapshot subvolumes, and for instance) roll back to older snapshots either by shuffling subvolume names using mv or by changing the subvol= option in fstab.

All this confirms that the posted fstab looks perfectly normal to me. Exactly like mine. 

There is no mention of /root in fstab (that's what the error message says) so something else is trying to mount /root somewhere and failing. What could that be? I've never seen that. I wonder if "unlocking my disk from the launcher" is the problem. Was the disk content encrypted? I've not done disk encryption so I don't know what goes on there. But I am sure that the problem is whatever it is that's trying to mount /root, not fstab itself.

---

### Post by tomheslinga on 2017-08-12
> **The Cog said:**
> There is no mention of /root in fstab (that's what the error message says) so something else is trying to mount /root somewhere and failing. What could that be? I've never seen that. I wonder if "unlocking my disk from the launcher" is the problem. Was the disk content encrypted? I've not done disk encryption so I don't know what goes on there. But I am sure that the problem is whatever it is that's trying to mount /root, not fstab itself.

The disk is not encrypted, so if there's no other option I'll backup my files and reinstall

In case this helps let me post the messages at boot from where it starts to go wrong;

```
mount: can't find /root in /etc/fstab
done.
Begin: Running /scripts/init-bottom ... mount: mounting /dev on /root.dev failed: no such file or directory
done.
mount: mounting /run on /root/run failed: no such file or directory
run-init:current directory on the same filesystem as the root: error 0
Target filesystem doesn' t have requested /sbin/init.
run-init:current directory on the same filesystem as the root: error 0
run-init:current directory on the same filesystem as the root: error 0
run-init:current directory on the same filesystem as the root: error 0
run-init:current directory on the same filesystem as the root: error 0
run-init:current directory on the same filesystem as the root: error 0
No init found. Try passing init= bootarg.
```

After this it goes on to load usb devices.
I should probably have posted this all before. My apologies for that. I was under the impression the other errors were simply a result of the first one..

---

### Post by #&amp;thj^% on 2017-08-12
I find this odd **"Target filesystem doesn' t have requested /sbin/init.**"
Have you ever run fsck on this drive? (I don't recommend it,  it's just a question.)
More here: [https://btrfs.wiki.kernel.org/index.php/FAQ#What.27s_the_difference_between_btrfsck_and_fsck.btrfs](https://btrfs.wiki.kernel.org/index.php/FAQ#What.27s_the_difference_between_btrfsck_and_fsck.btrfs)
Also have a look here: [http://marc.merlins.org/perso/btrfs/post_2014-03-19_Btrfs-Tips_-Btrfs-Scrub-and-Btrfs-Filesystem-Repair.html](http://marc.merlins.org/perso/btrfs/post_2014-03-19_Btrfs-Tips_-Btrfs-Scrub-and-Btrfs-Filesystem-Repair.html)

---

### Post by tomheslinga on 2017-08-12
Sorry, I don't understand. Isn't the check I did the right one? Marc's blog mentions: "btrfs check --repair, aka btrfsck"

---

