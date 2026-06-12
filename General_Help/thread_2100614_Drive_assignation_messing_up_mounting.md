---
title: "Drive assignation messing up mounting"
date: 2013-01-02
forum: General Help
---

### Post by nainsurvolte on 2013-01-02
Hi,

I am in the process of building a file server and for the moment I am  also salvaging data from a failed array. So I do connect and disconnect  some drives depending on what I am doing with some of them ( mostly  doing scan in parallel with another PC)

But most of the drives are not moving even in the SATA connectors but  still, the sd_ names of the device are constantly changing making reboot  a pain as it tries to find previous drive configuration.

For fstab, the drives are called by UUID, except for an array of btrfs  drives where it is called by UUID but have a string enumerating the  devices as such as explained in this wiki at the complete end of the  page.
[https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

So in this case, every time I restart with some drive disconnected or  new drive connected, I have to edit the fstab to change the /dev/sd_  specified in the btrfs array and then remount with
```
sudo mount -a
```So 2 questions comes to my mind
1) Is there a way to force some drives to always be /dev/sda or any other one so that I don`t mess up the arrays?
2) I read in some place that if fstab is the file for drive  configuration. mstab is for raid configuration (unless I misunderstood),  but most of the array I have are not even listed there, so is there  another file or place where raid, array configuration is kept?

Thanks.

---

### Post by TheFu on 2013-01-02
I don't know anything about BTRFS - tooooooo new for my data. Heck, we're still considering if ext4 is safe enough to migrate towards.  ***New* is the enemy of *stable*.**

I think this is a btrfs problem since mdadm has a /etc/mdadm/mdadm.conf file that supports UUID-based RAID member disks.

I don't know, but there may be a way to control sdX names under /etc/udev/  .... somehow. That is where the ethX problems got solved.

Sorry I don't have any useful information. Definitely an interesting issue.

---

### Post by nainsurvolte on 2013-01-02
The 2 new Btrfs drives aside, the same behavior applies to all my other drives which are either ext3 or ext4. As windows consider the Windows drive to be C:\, I would expect Ubuntu (Linux) to consider my system drive to be /dev/sda, which is almost never the case when I connect new drives. 

If only I could make sure that some of those drives stay the same, the Btrfs ones would inherit the same dev names, a bit like I am doing with static IP addresses on the network.

And as stated, if I go in mdadm.conf, I only have one raid array defined and it is the default one (md0). If I do
```
sudo fdisk -l
```

I can see a md127 array and in the Disk Utility (palimpsest) I have an array called 1, and both are nowhere to be seen in mdadm.conf or mtab. Any clue as to other configuration files that my hold a piece of that information or how Ubuntu get those array in its configuration?

---

### Post by TheFu on 2013-01-02
One thing I learned recently is to use **parted -l** and not fdisk. parted is 4K sector and GPT and MBR partition aware.

I'm still confused that you have issues with UUID-based fstab files?  I've never had that issue even when swapping SATA cables. Very interesting.

I've always manually modified the mdadm.conf file.  Don't think we are supposed to touch mtab.

Perhaps if you posted the conf files that are causing issues?

---

### Post by nainsurvolte on 2013-01-02
Maybe this is my issue, my fstab is badly done or missing some features.

Here it is

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e5f02341-4141-4780-9c62-2a3767fb9818 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff1d4514-0085-42c8-ada7-a09525a10728 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
0
UUID=7183d6ce-59c8-4310-bd04-6a9de5d5deb2    /media/tvrecordings/    ext4    errors=remount-ro    0    0
UUID=0286c1cb-735e-4f5f-9bf1-e0ba87725bf0    /media/master-data    btrfs    device=/dev/sdd,device=/dev/sde,compress,space_cache,inode_cache    0    0
```

Don`t mind the last line which is for the Btrfs drive.
1st drive is system drive, second, the swap on the same phyiscal drive and the third is the Mythtv recording drive, another physical drive.

 I will take note of the parted advice for the future.

---

### Post by TheFu on 2013-01-02
> **nainsurvolte said:**
> Maybe this is my issue, my fstab is badly done or missing some features.
Here it is
```
# /etc/fstab: static file system information.
UUID=0286c1cb-735e-4f5f-9bf1-e0ba87725bf0    /media/master-data    btrfs    device=/dev/sdd,device=/dev/sde,compress,space_cache,inode_cache    0    0
```Don`t mind the last line which is for the Btrfs drive.

I will take note of the parted advice for the future.

So you are saying that the boot drive doesn't work every time?  Are you certain where grub is installed - I mean, are you positive which drive?  Clearly, that drive cannot change unless you tell the BIOS which should be booted.  boot-repair should fix that issue.

Swap should never be a real problem on a new system today unless it is RAM constrained. Heck, most of my VMs don't get any swap at all.

That leave me with the btrfs line, which you said to ignore.  As long as you specify the sdX in that line, you do not have any hope of solving the issue.  Find a way to refer to an external config file that supported UUID-based HDD references. That's your only hope, Luke. ;)

Would using labels work?  [https://wiki.archlinux.org/index.php/Persistent_block_device_naming#by-label](https://wiki.archlinux.org/index.php/Persistent_block_device_naming#by-label) seems to say we can create our own labels and mount based on that.  You've probably already tried that method. Just a thought.

As to the parted stuff ... I didn't think it was important to me either, until new HDDs showed up that were 4K, but were not clearly marked as 4K sector drives.  Any new PC that arrives will probably have GPT partitioning, not MBR too.  In theory, the first 4 primary GPT partitions are compatible with MBR ... in theory.  Never trust theory when multiple vendors are involved.

---

### Post by nainsurvolte on 2013-01-02
> So you are saying that the boot drive doesn't work every time?  Are you  certain where grub is installed - I mean, are you positive which drive?   Clearly, that drive cannot change unless you tell the BIOS which should  be booted.  boot-repair should fix that issue.
Ok, I think there was some confusion. It boots ok every time for the two drives I was referring to. My issue is that the name of the device always changes. System drives is sometime /dev/sda, sometimes something else. As of nowm it is /dev/sdf. In the end, because they change, the btrfs mount change as well, which causes me issues.

I am not aware of any way to substitue the /dev/sd... in the btrfs line. In fact, this line was literally copied as suggested by some other peron on the forum who has lots of late under his name  ;). I guess I will dig on the net for more information on that and the importance of that string.

I will also look at that label thing. Despite the technical aspect of my question, I am only starting to go deeper into linux lately as my problem gets specific to a point I can`t find any answer to my problem or at least not as easily as before. Most of my knowledge come from 1 year of forum and internet digging in order to have a working MythTV, + 5 years to work on Unix machine back in the days where top of the class engineering software worked hand in hand with the different Unix OS on the market at the time (sgi, AIX, HP-UX and Solaris).

If after a few months I cannot find an answer, I'll drop it... if not, I'll post the answer hoping it can help others.

---

### Post by TheFu on 2013-01-03
No problem whatsoever.  I'm often confused. ;)  There is no cure, according to my SO.
The issue you are seeing is why /dev/disk/by-* maps where created.  You are not the first to have this issue by any means.

Labels, paths and UUIDs do not change even if the raw device does. THAT is the reason Debian/Ubuntu switched to those around 9.10-ish, if my memory is correct. I suspect all Linux systems made that switch in 2009, but I do not KNOW for sure.

The /dev/.../by-path method will never change unless you swap cables around. That is closer to the way that UNIX systems handle SCSI disk and HBA mappings too.  UUID and Labels shouldn't change even if you swap cables.  I was a sysadmin for Solaris, SunOS, HP-UX, AIX, OSF/1, Irix, Linux and a few others over the years. Disk management is always a little different on every platform, unless an expensive 3rd party vendor (usually Veritas) was deployed.

With all my years running Linux systems, I've never gotten MythTV working acceptably, so you should be commended on that achievement. My TV-tuner hardware was never well supported by Myth, hence my problems.

All is good.

---

### Post by nainsurvolte on 2013-01-03
So, I have asked the person from whom I have got the suggestion to use the btrfs filesystem, we will see what come out of that. I hope it wont be that it always worked for him... because it won`t really help me. Or maybe I will end up in the hardware section since my drives are all connected to 2 PCI Sata controller card.

Labels are a no go... here, directly from the btrfs.wiki
> The label on a filesystem can be set at creation time, using the -L option to *mkfs.btrfs*. 
You can also use *btrfs* command. There are currently few limitations: 
 
[LIST]
[*] the filesystem has to be unmounted
[*] the filesystem should not have more than one device
[/LIST]


... and since my filesystem has 2 devices...

On a side note... I have to admit that setting up my server with MythTV hasn't been a walk in the park even if I started with MythBuntu. At least, to have it setup the way I wanted it. For the TV tuner, have you tried HD Homerun, works like a charm, although I never managed to make it work with TVHeadend, which has better connectivity with XBMC...

---

### Post by TheFu on 2013-01-04
> **nainsurvolte said:**
> So, I have asked the person from whom I have got the suggestion to use the btrfs filesystem, we will see what come out of that. I hope it wont be that it always worked for him... because it won`t really help me. Or maybe I will end up in the hardware section since my drives are all connected to 2 PCI Sata controller card.

Thank you for beta testing BTRFS. I appreciate it. There are still major issues with data loss extremely possible.  

I'm still using JFS and EXT3 on some storage - **new is the enemy of stable.  **New boxes are using EXT4, but that just started a few months ago.  I like to wait a few years after everyone else switches before going to new file systems. My data is too important to risk with anything less than 100% proven file systems. For very large data, I'd probably still deploy XFS instead.  If btrfs were perfect today, I'd consider deploying it in 2016.  

Mixing btrfs AND mdadm is another complexity.

> **nainsurvolte said:**
> On a side note... I have to admit that setting up my server with MythTV hasn't been a walk in the park even if I started with MythBuntu. At least, to have it setup the way I wanted it. For the TV tuner, have you tried HD Homerun, works like a charm, although I never managed to make it work with TVHeadend, which has better connectivity with XBMC...

I have an HDHR3 and **love it!**  But when I was trying Myth, I was using an ATI TV Wonder card with a bt787. Then with a USB 950Q, which didn't have Myth support for a few more years.  When Windows7 arrived, the media center supported QAM recording out of the box with the 950Q. While not perfect, it worked. Running Windows always bothered me, but free schedules and a free Win7Ultimate license (thanks MS!) meant I could without cost.  Playback happens using XBMC on Linux or using a WD TV device over the network. Both are silent, which is critical to me.  After getting the HDHR, I moved the Win7 install into a KVM VM - networked tuners rock.  That was about 18 months ago. [http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm](http://blog.jdpfu.com/2012/02/06/running-windows7-media-center-inside-a-kvm-vm) explains. After the initial disk and network performance issues were solved, only 1 recent issue since then. A windows update prevent an RDP connection from opening the 7MC app.  I'm forced to use a console.  I digress for this thread.  

I did try to get tvheadend working under XMBC, but only with an OTA antenna. Something was lost in the complexity of the setup - never saw any channels.

Back to the drive issue ... non-motherboard SATA ports tend to jump around.  I've seen that with my RAID cards in JBOD mode. You've got to use the /dev/disk/by-*  whatever methods to address each disk. There is no other way. If btrfs doesn't yet support that, you need to switch to a different file system.  I'd recommend a new question specifically titled "**btrfs disk labels with mdadm**" to get more targeted help. A good title matters in these forums.

For that amount of storage, if you want/need advanced file system functions, perhaps a ZFS deployment would make more sense?  ZFS is my dream file system, but it isn't easily deployed on Linux (at least not easy enough for all the servers I'd need). I think it is getting better for deployment now.

---

### Post by nainsurvolte on 2013-01-04
> Back to the drive issue ... non-motherboard SATA ports tend to jump  around.  I've seen that with my RAID cards in JBOD mode. You've got to  use the /dev/disk/by-*  whatever methods to address each disk.

Just Googled the /dev/disk/by-id, did not knew about that, so it will definitely be a reading for tonight. Seems promising though...

> f btrfs doesn't yet support that, you need to switch to a different file  system.  I'd recommend a new question specifically titled "**btrfs disk labels with mdadm**" to get more targeted help. A good title matters in these forums.

Definitely, I was trying to edit the title yesterday, but could not. I was thinking about editing the first post in the thread to specify the real issue.

> For that amount of storage, if you want/need advanced file system  functions, perhaps a ZFS deployment would make more sense?  ZFS is my  dream file system, but it isn't easily deployed on Linux (at least not  easy enough for all the servers I'd need). I think it is getting better  for deployment now. 	

It was my first choice after a few research on the net to find a reliable and secure file system. It had redundant functionality built in regardless of the size of the drives, what more do you want.... But what discouraged me is that it says it requires a lot of RAM... which I don't have a cannot have. Currently the machine has 1GB and could extend to 2 GB. Also, as you mentioned, limited integration out of the box for Linux. 

The reason I went for Btrfs is that it is a close relative to Zfs ( lots of questions comparing both on the Btrfs wiki) and it does not require a lot of ram. Lot of people say that if you are not trying weird things with the File system, it is pretty reliable. And in the end, the biggest portion of the data I have is backed up with one of my friend. We call this "Natural backup". The only thing I need to do is backup all the personal stuff (photo, family video, music...) for which I will create a Raid 1 and use external disks.

Like you, I never managed to make the channel appear in TVheadend, scan were giving nothing.

See you around, and if you have question regarding MythTV, i'll do my best to help, although my setup is pretty simple, only connected OTA. I'll also look at your link, did not understand what you said so, need to read it. ;)

---

### Post by nainsurvolte on 2013-01-04
Got it....

Answer is here.

[http://article.gmane.org/gmane.comp.file-systems.btrfs/2534/match=btrfs+fstab](http://article.gmane.org/gmane.comp.file-systems.btrfs/2534/match=btrfs+fstab)

After much research (thanks to TheFu for the last hint that got me in the right direction, /dev/disk/by-id), issue came from these factors

1) the drives are connected through 2 different PCI Raid controllers with SATA connectors. Apparently, device names through those can be a bit more random than through port on the board. But then again, when connecting a USB drive, it was still  taking the /dev/sda instead of my root drive connected to SATA 1 on the board...

2) Problem was impacting the Btrfs array that I have. 

To mount an array you need a line in fstab as described in the wiki 

```
/dev/sdb     /mnt    btrfs    device=/dev/sdb,device=/dev/sdc,device=/dev/sdd,device=/dev/sde    0 0
```

You can substitute the /dev/sdb, by the UUID of the Btrfs array using the blkid (drives in the array will have the some UUID but different Sub UUID, theirs...).

The funny thing is that although you can declare the array by the UUID, the portion of the mount line in fstab (bold)

```
/dev/sdb     /mnt    btrfs    **device=/dev/sdb,device=/dev/sdc,device=/dev/sdd,device=/dev/sde**    0 0
```

cannot handle UUID, but it can handle /dev/disk/by-id (again Thanks Thefu for that aspect I did not knew about). Therefore, the mount line for the array now looks as such

```
UID=0286c1cb-735e-4f5f-9bf1-e0ba87725bf0    /media/master-data    btrfs    device=/dev/disk/by-id/scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T0394254,device=/dev/disk/by-id/scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T0471399,compress,space_cache,inode_cache    0    0
```

Its one hell of a line, but I unmounted and re mounted the array and everything works...

Problem solved

---

