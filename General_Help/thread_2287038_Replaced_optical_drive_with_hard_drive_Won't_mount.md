---
title: "Replaced optical drive with hard drive: Won't mount on boot"
date: 2015-07-16
forum: General Help
---

### Post by Bucky Ball on 2015-07-16
Hi all,

Odd problem. I just bought a hard drive bay which replaces the optical drive and bay in a laptop. Got it home, pulled my optical drive out, chucked an old 80Gb drive in the new HDD replacement bay, fitted that in the optical drive slot, switch on and all is well. Hard drive is seen and mounts. Gparted sees it no probs as sdb and the partition (just one partition on the drive) as sdb1. My laptop now has two drives! Excellent! 

Except ...

When I click the hard drive in the file manager (PCmanFM) it asks for a password to mount it, then mounts it in /media/user/80GbHardDrive. Hmm. That seems normal, but not sure about the permissions bit. (For the record I have an eSATA external drive that has exactly the same issue and, while I was able to fix this in 12.04 by creating an esata rule, it doesn't work in 14.04.) 

Not to worry, I'll write it up in fstab and get it to mount where I want it. So I create the mount point /mnt/80g and edit fstab to include this:

```
#sdb1
UUID=f4882fcc-17d9-4047-87d0-0b02af4eb988       /mnt/80g        ext4    errors=remount-ro       0       1
```

This line, apart from the mount point and the UUID, are the same as the others I have for EXT4 partitions. Everything looks normal. I reboot and get a message that 'there is an error mounting /mnt/80g'. ? I quadruple check that everything is correct - UUID, mount point - and it is. 

So what is happening? I had a think whilst doing the dishes and perhaps, somewhere in the system, what was the optical drive connection is expected to give the optical drive's UUID, etc., but what was the ODrive is now a HDD with a different ID. I never had an entry for the optical drive in fstab (and the Odrive worked fine anyway) so perhaps that is at the bottom of this.

Any help greatly appreciated. Just ask for further info. There is no problem mounting this via the terminal, incidentally ('sudo mount /dev/sdb1 /mnt/80g' works fine), so it is working fine and usable. It is only the fstab that won't mount it and throws an error and as this is now an internal drive I want it mounted at boot (or at least I'd like to get rid of the permissions issue when I click on it, that would be an okay solution, too). 

:-k

PS: For those of you who may be confused about the optical to HDD conversion, [this is what I'm talking about]("http://www.silverstonetek.com/product.php?pid=323&area=en"). The exact unit(s). It's working great so far, apart from this, and 'out of the box'. The 80Gb hard drive I'm using has been around awhile in all sorts of roles so might be a permission thing. I'll dig deeper into that.

---

### Post by dino99 on 2015-07-16
i'm not sure at all, but behind the bay there is a chipset to monitor the optical device; and now that specialized chipset is confused and think about a remote device (only my own imagination, can be wrong)

maybe lshw and/or logs could bring some comments

---

### Post by Bucky Ball on 2015-07-16
```
 *-disk                  
       description: ATA Disk
       product: TOSHIBA MK3263GS
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: FG02
       serial: 20B3FD6US
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=f4a0f721
  *-disk
       description: ATA Disk
       product: ST980811AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 3.BH
       serial: 5LY20W7B
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=2fa94dae
```

Doesn't appear to be anything out of the ordinary there, unless the bus info on sdb should be scsi@2:0.0.0 and not scsi@5:0.0.0.

I'm going to see if changing permissions on the partition makes a difference shortly.

---

### Post by oldfred on 2015-07-16
I have always use Morbius1 template for fstab entries.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.


 UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

But I think you need defaults or relatime
For info on mount parameters:
man mount 

Then I normally have data partitions and want similar settings to /home.
      
        
 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by sudodus on 2015-07-16
> **oldfred said:**
> ...
But I think you need defaults or relatime
...

+1

Or maybe this HDD is a slow starter, and you should delay the boot process maybe 5 seconds or more to make it work.

---

### Post by Bucky Ball on 2015-07-17
Thanks for the input all. I'm going down this path.

When I remove the entry for the new sdb1 partition from fstab, reboot, the partition is listed in PCmanFM as '80GbDrive', which is what Gparted tells me the label of sdb1 is and you can see in the first attached screenshot. All good. Happy to just have it mount when I click, no need to mount at boot really. 

I click the partition in the file manager and get the error in the second screenshot attached. Note: This is exactly the same problem I have had with my eSATA external drives since 14.04 LTS now happening with an internal SATA drive. I have never been able to solve the eSATA issue. Spent hours and have even [written a how-to]("http://ubuntuforums.org/showthread.php?t=2161837&p=12728219#post12728219") for 12.04 LTS which no longer works for me in 14.04.  

If I do authenticate and mount the partition, it creates a mount point in /media/<user>/80GbDrive. So I figured it was permissions. I tried the command from oldfred:

```
 sudo chmod -R a+rwX,o-w /media/<user>/80GbDrive
```

... and also tweaked the fstab using the method suggested: ext4 defaults,noatime 0 2, proceeded by sdb1's UUID. All my other partitions have been mounting okay with the way I posted earlier, and unfortunately, changing the entry for sdb1 didn't help. Same as original error.

Oddly, if I create the mount point /media/<user>/80GbDrive and reboot, sdb1 (80GbDrive) won't use it and mounts itself as /media/<user>/80GbDrive1 ... ! :-k 

Is there something obvious I'm missing? Am I trying to change permission on the wrong directory or using the wrong command?

PS: Just checked and also get asked to authenticate with Thunar.

PPS: A last note: On my how-to for esata there is a paragraph at the end about this being a minimal install specific issue. I wonder what software would fix this from the desktop version? I only use the minimal install and my desktop has this issue also. :-k

---

### Post by oldfred on 2015-07-17
If you mount in /media with fstab, it shows twice in Nautilus. The second mount with the _ is then invalid as you can only mount once.
So I always mount in /mnt, but link folders, so I do not have to drill down thru computer, mnt to find my files.

You reset permissions, but did not reset ownership with chown?

---

### Post by Bucky Ball on 2015-07-17
> **oldfred said:**
> If you mount in /media with fstab, it shows twice in Nautilus. The second mount with the _ is then invalid as you can only mount once.
So I always mount in /mnt, but link folders, so I do not have to drill down thru computer, mnt to find my files.

You reset permissions, but did not reset ownership with chown?

Tried mounting in /mnt. No different. When I boot up, it want to mount itself in /media/<user>/80GbDrive 'automagically'. When I click it that's where it goes.

If I mount it manually with, say:

sudo mount /dev/sdb1 /mnt/80g

It mounts without issue. I can mount it wherever I like, actually, with no issue whatsoever. 

So, when I boot the machine the partition appears in file manager as '80GbDrive'. I can manually mount it wherever I like, but if I just click it it creates it's own mount point in /media/<user>, even if I create the mount point '80GbDrive' it will simply not use it and create another. 

I will try chown-ing it (I think I did that too but been away from it for awhile). The difficulty with this is that it creates a new mount point so chmod-ing and chown-ing is a bit superfluous as it doesn't use any mount point I create and change ownerships to anyhow. :-k

Tnx again for the input.

---

### Post by NoWayWin8 on 2015-07-17
> **Bucky Ball said:**
> 
Is there something obvious I'm missing? Am I trying to change permission on the wrong directory or using the wrong command?
Did you try creating a mount point of /media/80GbDrive
```
$ sudo mkdir /media/80GbDrive
```
Then in fstab:
```
/dev/sdb1     /media/80GbDrive   ext4    defaults     0 2
```(replacing 'defaults' with preferred options)
More info [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by Bucky Ball on 2015-07-17
Read the thread. Yes. :)

No entry in fstab works, regardless of where you make the mount point or details you set up the line with. It appears as '80GbDrive' and mounts in '/media/<user>/80GbDrive. It doesn't want to know about anything else, regardless of how I might try and persuade it. 

Bottom line: regardless of what I put in fstab or where I try to mount it, or with whatever I put at the end of the fstab line, it ignores and throws an error at boot with the mount point in fstab. 

PS: /dev/sdb1 in fstab is antiquated. UUIDs are used now. See my first post.

PPS: [This]("http://ubuntuforums.org/showthread.php?t=2287239&p=13323041&viewfull=1#post13323041") actually looks kinda similar as far as the partition creating its own mount point and not wanting to mount anywhere else, regardless of what I do manually (remembering that if I do create a mount point and manually mount the partition sdb1 prior to clicking on the partition and letting it do its own thing there are no problems. It mounts where I tell it to. Just not if I tell it to in fstab. :-k

---

### Post by Bucky Ball on 2015-07-17
Progress. I created the mount point /media/<user>/80GbDrive and put this line in fstab:

```
UUID=f4882fcc-17d9-4047-87d0-0b02af4eb988       /media/<user>/80GbDrive        ext4    defaults,noatime        0       2
```

On boot, same error 'There was an error reading partition for /media/<user>/80GbDrive', or something similar. Under that I could hit 's' for skip (which is what I normally do), 'm' to fix manually, or a new one, 'f' to fix. I hit 'f' and the computer made a few whirring noises and once at a desktop, open file manager and voila, fixed. There is the partition mounted in /media/<user>/80GbDrive. 

Consider this solved. Thanks for the input. ;)

PS: Now if only I could figure out how to get my external eSATA dock to do this when I plug it in. Trying to fix that has been the 'never ending story'. I fiddle with it and give up again when I start going in circles, again, every six months or so.

---

### Post by oldfred on 2015-07-18
It seems like partition may have needed fsck?

Did you set both permissions & ownership based on new mount point.
 sudo chmod -R a+rwX,o-w /media/$USER/80GbDrive
 sudo chown -R $USER:$USER /media/$USER/80GbDrive

---

### Post by NoWayWin8 on 2015-07-18
> **Bucky Ball said:**
> Read the thread. Yes. :)
I thought I did carefully. I must have misinterpreted this:
> Oddly, if I create the mount point /media/**<user>/**80GbDrive and  reboot, sdb1 (80GbDrive) won't use it and mounts itself as  /media/<user>/80GbDrive1 ... ! 

---

### Post by Bucky Ball on 2015-07-18
> **oldfred said:**
> It seems like partition may have needed fsck?

Did you set both permissions & ownership based on new mount point.
 sudo chmod -R a+rwX,o-w /media/$USER/80GbDrive
 sudo chown -R $USER:$USER /media/$USER/80GbDrive

Not sure if needed fsck as there was nothing wrong with partition if I mounted it manually via a terminal and 'mount /dev/sdb1 /media/<user>/80GbDrive'.

Since doing that fix I haven't needed to do anything to change permissions. You may have read my post prior to my edit. I was trying to drop the file in '/media/<user>' directory, which gave me the permissions problem, rather than '/media/<user>/80GbDrive', where there is no permissions problem and the file drops on without issue. :)

I might try fiddling with the eSATA dock later and see if I can work some magic by creating the mount point the external eSATA partitions create 'automagically' when I mount them and changing permissions on them, as you suggest oldfred, and seeing if they mount there when I click them. Wish me luck. That would be cracking a nut that just wouldn't crack for the last X years. I have tried a lot of things to fix eSATA over the years, but since 12.04 LTS, none of them have worked. Stuff of another thread ...

---

### Post by dino99 on 2015-07-18
Maybe check the bios/uefi hdd/pci settings, and experiment a few tweaks
then if you fail to find a solution via the bios settings, maybe check with ubuntu vs xubuntu, to know if xub settings need some fixes.
and about the installed kernel(s), do you install the ones found into the archives ? or vanilla ones, or your custom builts ?

---

### Post by sudodus on 2015-07-18
> **Bucky Ball said:**
> Not sure if needed fsck as there was nothing wrong with partition if I mounted it manually via a terminal 

Maybe there was a deadline to check the partition (that can be set and checked with tune2fs), and it had passed that deadline for checking, so it 'wanted' checking (even if there was no error).

---

