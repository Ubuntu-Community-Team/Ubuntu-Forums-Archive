---
title: "getting rid of dual boot"
date: 2013-10-01
forum: General Help
---

### Post by Dermot Doyle on 2013-10-01
Hi,
I have managed to get myself into a mess with my Dell 17R running 12.04. Despite being on the canonical list of suitable computers for Linux there is a serious problem with the fan control in that there isn't any. Something to do with integrated graphics cards and fan speed controlled by the BIOS with little or no support. I finally managed to work around it using i8kctl, which manually slows the fan speed. Now, due to another problem, I dual booted my laptop with another version of 12.04 (it's a long and sad story) and now the i8kctl rarely works. The fan speeds up and slows down randomly. Opening a terminal and typing in 'i8kctl fan 1 1' slows it for a couple of seconds and then it slowly speeds up and rattles horribly. I assume the second install has upset the little control I had over the fan so what I want to do is get rid of the second, dual bootted 12.04. I have seen a couple of guides, but neither of them worked. I have to admit that I am not very computerate and it was probably me getting things wrong that made them fail. Can anyone give me a simple, idiot proof step by step guide to getting rid of the dual boot? If not I suppose I'd have to wipe it and start again or throw the thing in the bin where it belongs and never buy a Dell again. Sorry for the long post, there's a hell of a lot more info I left out.
Thanks,
Dermot

---

### Post by tfrue on 2013-10-01
What I would do is boot Partition Wizard either from usb or cd and try to remove the partitions that you created with the second install. But, I would assume it depends on how you installed both of the versions of linux. Anyway, if you don't have any precious data on the drive, then I would just re-install and start over because that will more than likely be the fastest way to fix your problem, and if you do have files you need, just back them up to an external drive and then re-install. When you installed the second machine did you manually do it or did Ubuntu walk you through it? If you were walked through it then like I said, boot Partition Wizard and remove the second install, if you would rather remove the partition from linux try; 
user@ubuntu: sudo fdisk -u /dev/sda (which should show a list of partitions on your hard drive and you should determine which partition has the second install and remember the number)
user@ubuntu:d (you will be asked which partition number you want to delete, I don't have a system I can show you for testing right now sorry :/ )
user@ubuntu:w (which will write the changes to hard drive and hopefully that solves the problem. )

There are more options to remedy this but like I said, it will probably be easier for you to format and re-install and maybe purchase an inter-cooler for your laptop since you're having problems with the fan.

I hope this help at all, if you want me too I will install Linux on a hard drive and show you how the fdisk works, but it's late in my part of the States, and I'm going to bed lol, so good luck!

---

### Post by Dermot Doyle on 2013-10-01
Hi, thanks for the quick reply. I tried sudo fdisk -u/dev/sda and got this:

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

I have no idea what this means, I simply pressed q to quit. No list of partitions. I did simply let Ubuntu walk me through the second install so I'll try Partition Wizard. Otherwise a complete new install. I have done this a few times before, but I have to admit my heart is in my mouth when I do since I assume it will go horribly wrong somehow and I'll spend hours on the forum fixing things.
Thanks again for the help

---

### Post by Dermot Doyle on 2013-10-01
Just discovered I have Disk Utility already loaded in my software. Can I use that or is it not a good idea? Also I have no idea which is my first instillation which I want to keep and which is the second I want to get rid of. I tried and failed to add a screen shot to make it clear. I know that I used around half of the capacity for the second install so I can't tell simply from the size and I don't understand the information as it is presented in the Disk Utility window. Sounds a bit pathetic, but I really am not very good at this stuff. Any suggestions gladly received.

---

### Post by ajgreeny on 2013-10-01
We really do need to know which partition is which, so can you run the commands ```
sudo fdisk -l
``` and ```
mount
``` and report the output of those back here in code tags please, (the # in the toolbar of the reply window). 

I hope that will show us all that is needed to be able to tell you which partitions to remove.

Disk Utility will also show you which partition is which, and what the mountpoint of each is from your running system, but the fdisk command will show everything listed and may be more useful.

---

### Post by Mark Phelps on 2013-10-01
You did > sudo fdisk -u/dev/sda -- with no space between "-u" and "/dev".  You need a space there, as in > sudo fdisk -u /dev/sda Also, add the "l" parm (lowercase L, not a one) to make it > sudo fdisk -lu /dev/sda

---

### Post by Dermot Doyle on 2013-10-01
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001045a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1058585588   529291770+  83  Linux
/dev/sda2      1058586622  1953523711   447468545    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1941198848  1953523711     6162432   82  Linux swap / Solaris
/dev/sda6      1058586624  1941198847   441306112   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     7821311     3910640    b  W95 FAT32

```

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001045a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1058585588   529291770+  83  Linux
/dev/sda2      1058586622  1953523711   447468545    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1941198848  1953523711     6162432   82  Linux swap / Solaris
/dev/sda6      1058586624  1941198847   441306112   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     7821311     3910640    b  W95 FAT32
dermot@dermot-Inspiron-5721:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/dermot/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dermot)
/dev/sdb1 on /media/4A17-DA6C type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

```

Hi ajgreeny, this is what I got.
Hi Mark, thanks. I'll see where I get with the above stuff first.
Dermot

---

### Post by oldfred on 2013-10-01
Did you install sputnik. That is the extras that Dell has for its Ubuntu systems.
 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

I do not have Dell but someone posted that all of Sputnik is in the 13.04 version.

---

### Post by Dermot Doyle on 2013-10-01
Hi oldfred,
No I haven't installed sputnik, I'd never even heard of it. When I phoned Dell Support about the fan they said Ubuntu wasn't supported and I'd invalidated my warranty. They certainly never mentioned it. From what I've read I guess I could install 13.04 if I do a fresh install, but if I could only get rid of my second OS and get control of the fan again it would be the path of least resistance for someone like me with limited computer skills (and little faith in technology). Thanks for the heads up, I'll see how I go with getting rid of the partition and go from there.

---

### Post by poettone on 2013-10-01
Dermot,

I've been in your position in the past and from your output it seems that it might be best if you simply start over from scratch as it seems you have two linux installations, one without a swap partition which is necessary for your linux system to function correctly. it also appears you have an old windows drive /sdb that is 4gb in size. 

Although it seems you have multiple issues on this system, regarding your fan I would first make sure your cpu heatsink is clean and dirt free as the system fan will turn on and off as a system heats up and cools down. if you have a fan running all the time I would suspect something like this. If you have checked this out already then regarding that we could look at something else regarding that issue. For now though I would recommend starting over with one installation of Ubuntu, removing the 4gb windows drive and not even use it as it's marginal from a 'space" perspective with your corresponding 1TB drive installed. 

Good Luck.

---

### Post by poettone on 2013-10-01
Dermot,

I've been in your position in the past and from your output it seems that it might be best if you simply start over from scratch as it seems you have two linux installations, one without a swap partition which is necessary for your linux system to function correctly. it also appears you have an old windows drive /sdb that is 4gb in size. 

Although it seems you have multiple issues on this system, regarding your fan I would first make sure your cpu heatsink is clean and dirt free as the system fan will turn on and off as a system heats up and cools down. if you have a fan running all the time I would suspect something like this. If you have checked this out already then regarding that we could look at something else regarding that issue. For now though I would recommend starting over with one installation of Ubuntu, removing the 4gb windows drive and not even use it as it's marginal from a 'space" perspective with your corresponding 1TB drive installed. 

Good Luck.

---

### Post by Dermot Doyle on 2013-10-01
poettone,
I suspect you're right. I'm sure it's not a dirty heatsink or fluff in the fan filter, it has behaved like that since the day I got it and installed 12.04 (I am a bit pissed off with canonical since they include the 17R in their list of supported laptops, but this is a serious and easy to spot problem). I wanted to dual boot it with the windows 8 it came with (sod it, I'd paid for it after all) but it would appear that windows 8 has been written with specific blocks to stop you dual booting it with anything else. So I followed the Ubuntu disc and did what it said. I don't know why it left some windows stuff or why something wasn't correctly partitioned. I am completely at the mercy of the install disc. The fan issue is well known as I have discovered, but as I say I did manage to at least turn it down through a terminal command. Thanks for taking the time.
Dermot

---

### Post by ajgreeny on 2013-10-01
I think sda1 is your root partition of the ubuntu you are running successfully, as that is the one with the asterisk on it in the fdisk printout, but that assumes you were running that version when you used that command. You can forget about only having one swap with two OSs, as both will use the one swap without a problem.

So - -, backup all your files if you've not already done so, then boot to your good ubuntu and run ```
sudo grub-install /dev/sda
```Now boot to your live system again and run gparted.  When the window shows, right click on swap and choose "swapoff" then unmount the extended partition sda2 from the same gparted window.  Now you will be able to delete the sda6 partition, and finally reboot.

---

### Post by Dermot Doyle on 2013-10-01
Yes, I was using my successful version of 12.04 when I used the command. I'll be getting my external hard drive back in a couple of days and will back up my files and do as you suggest. I have just installed gparted from the software centre since I didn't have it. When you say boot to your 'live' system again after the terminal command I assume you mean the successful original install again. Is that right? 
Cheers

---

### Post by ajgreeny on 2013-10-01
Unless I'm carrying out operations on partitions which are on either another physical hard disk, or on a USB disk or memory card, I would always use gparted when booted to the live DVD or USB used for installation, which has gparted installed by default.  You could do it from your installed ubuntu OS with gparted, since you have already installed it.

If you use a live OS you will still need to use *swapoff* and then unmount the extended partition, as a live system will find and use swap if it exists.

After you have deleted the sda6 partition you can make a new ext4 partition in its place to use as a data partition, ie, just for storage.

---

### Post by Dermot Doyle on 2013-10-03
Hi ajgreeny,
Thanks for your help so far. Bizarrely, my fan has started behaving itself, running quietly without my having to go into a terminal and turn it down manually. This hasn't happened since I loaded 12.04. In the great tradition of 'if it isn't broken, don't fix it' or rather 'if it isn't broken keep fixing it until it is' I'll leave well alone for now. If it starts acting up again I'll follow your advice on partitioning. I'll mark this as solved and only start a new thread if I have problems with the partitioning.
Cheers,
Dermot

---

