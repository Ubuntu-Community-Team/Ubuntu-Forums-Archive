---
title: "GRUB Problems &quot;error: unknown filesystem&quot;"
date: 2013-06-14
forum: General Help
---

### Post by jbo5112 on 2013-06-14
I have a Virtual Machine (in ESXi 5.1) running Ubuntu Server 12.04.  When I try to boot my system I grub2 tells me "error: unknown filesystem".  I've tried booting a Live CD then reinstalling grub from both a chrooted environment and by supplying the --root-directory option.  I've even tried a boot-repair CD (results [here]("http://paste.ubuntu.com/5765582/")) and reinstalling grub.  Whatever I use to fix it, I'm getting the error "Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting."

To complicate things I'm running a RAID5 array (5 disks) using mdadm and btrfs for my filesystem.  The btrfs tools that ship with Ubuntu 12.04 are really old.  I've added ppa:cjwatson/grub and ppa:yofel/btrfs to my software sources to get more up to date utilities, with no help.  The system was previously working before switching from a 4 disk RAID0 setup.  I think this was the first reboot since the upgrade, but it was running fine for weeks using RAID5.

I had the same problem on a similarly configured workstation running Linux Mint, but it magically went away after a failed grub-install or failed boot-repair.  I have no idea what actually made it work again, but it's fine now.

---

### Post by jbo5112 on 2013-06-17
Any help?  Do I need to file a bug report about this?

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]jbo5112;
As your query is old .. I will respond in order to keep it alive and visible. Be aware it is forum policy not to respond if one does not have something constructive for that thread. Most of us here are not familiar with the set up you have described and, like me, probably have no notion of how grub would interact in a virtual machine environment on top of raid. -> if you do not know, say nothing.

Ok, so you wait until someone does know, has the time. and has the inclination ( all here are volunteers ) to respond properly.
And yes, you may "bump" up your thread if no response in a 24 hour period to regain focus.
[INDENT=2]
no help, but try'n to make things better 
 [/INDENT]

[/COLOR]

---

### Post by jbo5112 on 2013-06-18
I'm getting a little closer.  I can reinstall grub2, but now, when I boot, it's telling me "error: no such device: <UUID for md0>."  Hopefully this makes the problem easier to fix.  I'm guessing md0 is failing to be built in the initramfs.

Step 1 is what eliminates the previous error, but here's everything I did.

**Step 1: Manually Update /boot/grub/device.map**
Old file
```
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde
```
New File
```
(hd0)   /dev/md0
```
**Step 2: Build new initramfs**
```
update-initramfs -u -k all
```
**Step 3: Update grub config**
The first command might not be necessary (found on a Gentoo forum)
```
grub-mkconfig
update-grub
```
**Step 4: Install grub**
```
for drive in /dev/sd?;do echo "Installing to ${drive}:"; grub-install $drive;done
```

---

### Post by grahammechanical on 2013-06-18
I did not realize that your problem involved a btrfs file system. A couple of us on the Ubuntu+1 section of the forum have been experimenting with btrfs. Grub does not work well with btrfs file systems.

If Ubuntu is installed on a btrfs file system and Grub is installed into the MBR at the same time then we see our Ubuntu+btrfs installation in the Grub menu and we can boot into it. But allowing some other Installation to put its Grub into the MBR will result in Ubuntu+btrfs not appearing in the Grub menu. Grub os-prober just does not detect Ubuntu on a btrfs partition.

You are in a Catch 22 situation. You need to install Grub into the MBR from the Ubuntu+btrfs install but to do that you need to boot into the Ubuntu+btrfs install. and Grub says: "Gotch yer!"

I have been in this situation myself. I have a single machine with 2 hard drives and several installs of Ubuntu, four of which are on btrfs. I have yet to boot into a Ubuntu+btrfs which did not appear in a Grub menu or from Grub rescue or Unknown file system error messages. I spent most of yesterday trying. I am now back in my saucy+btrfs on my second drive. I booted into raring+Ext4 on that drive and added a customised grub file to /etc/grub.d/ That put Ubuntu+btrfs back into the Grub menu. I booted into Ubuntu+btrfs and run grub-install /dev/sdb.

I suggest that you install Ubuntu+Ext4 into another partition on that hard disk and let it put Grub into the MBR. Then boot into Ubuntu+Ext4 and use /ext/grub.d/40_custom to create a customised file called 15_custom using the boot parameters of grub.cfg from Ubuntu+btrfs. then run

```
sudo update-grub
```
```
sudo grub-install /dev/sd??
```

That should put Ubuntu+btrfs into the grub menu which will allow you to boot into Ubuntu+btrfs. You can run those two commands from there and that may fix the problem. You could also try creating this 15_custom file using a live session.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

For your information: update-grub is a script that runs grub-mkconfig and update-grub2 is a link to update-grub. Whereas, grub-install copies Grub images into /boot/grub and uses grub-setup to install grub into the boot sector.

I have had instances of Ubiquity being unable to install Grub into the MBR. In this situation we need either a separate boot partition (not btrfs) or at least 1GiB of unallocated space before the first partition.

The problem here is not the lack of quality btrfs tools but a weakness in Grub os-prober and grub-setup. 

I hope some of this helps you.

Regards.

---

### Post by jbo5112 on 2013-06-19
I'm booting to the boot-rescue CD, which is a live CD running Ubuntu 13.04, so no catch-22.  When I boot, it's saying no such device, not a failure to read/mount device (not sure what that would look like in grub).  I don't think I'm currently having problems with btrfs.  Running grub-install no longer gives me any errors either.  Everything was fine before switching to RAID-5

---

### Post by matt_symes on 2013-06-19
Hi

You have a complicated setup on a new filing system where RAID 5 is not fully supported by BTRFS out the box yet so you are using software raid.

You may want to ask in #btrfs on freenode and see if anybody has the same setup as you, if no one here can help you.

You say it's working in Mint. I would compare and contrast the differences between the setups.

Kind regards

---

### Post by jbo5112 on 2013-06-20
I'm not sure what's different in Mint, other than Mint being a real desktop based on Ubuntu 12.10 (instead of 12.04).  I've installed the same ppa's for grub and btrfs-tools.  They're both running 3.5 kernels with the same grub and btrfs-tools.  I suppose it could be that my Mint workstation is running RAID-6 with a hot-spare disk, but it's probably not the deal breaker to switch to a RAID-5 system.  There could be something different in how the grub configuration is built, but since my goal is to develop some web-app tools (not patch OS bugs), the grub-2 config is more complicated than I want to dive into for just development.

Since it's a virtual machine, I gave up, took the easy way out, and I added a couple small virtual-disks to move /boot to a btrfs-raid1 array.  I suppose I'll wait for finished RAID-5 support in btrfs before fixing the hack.

Thanks for your help everyone! :)

---

