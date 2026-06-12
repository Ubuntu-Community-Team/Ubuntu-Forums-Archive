---
title: "LVM using multiple VGs for root installs"
date: 2023-07-02
forum: General Help
---

### Post by aljames2 on 2023-07-02
We know the installer's default LVM setup gives 1 PV (the whole disk), with 1 VG (spanning the whole disk), and LVs for /, & swap with the root LV sized to 100% of remainder after swap allocation.  We like to customize our partitions either before or immediately after install via Try Ubuntu.

I bring this thread up to avoid hyjacking this other thread, and to expand on what I think I learned:  [https://ubuntuforums.org/showthread.php?t=2487726](https://ubuntuforums.org/showthread.php?t=2487726)

My question is the idea shared in the link, regarding root installs, that of using separate VGs for /, /home, swap, & /data (i.e. 4 VGs as an example).  My understanding has been to place these in separate LVs inside a single VG?  Interesting, to instead do so in multiple VGs for the install.  Of course, there would an LV in each VG.  Am I understanding this possibility correctly?

I primarily think of VGs as being larger because they can span multiple PVs.  So, in thinking of VGs being potentially bigger than physical disks, I had not thought of VGs in revers, i.e. having smaller ones on a single PV.  I am sure this is my rookiness coming back here :)

I can see the benefits thought of multiple VGs on a single disk because there is more versatility w/VG changes than LVs.

---

### Post by ixeous on 2023-07-02
I generally like to put my "system" mounts /, /usr, /var, /tmp, swap into a single VG. I typically use VGsys as the name.  I sometimes add /home to that one b/c it's is so fundamental, but depending on the system use, it can be split out into a separate VG.  If the system is one that will have data storage, then I will create a VGdata for any mounts of that type.  I don't see much benefit to separating the various OS mounts into separate VGs.  A data mount is more likely to need to grow over time or to use snapshots as part of a backup.  The data can sometimes be /home.

---

### Post by Dennis N on 2023-07-02
> We know the installer's default LVM setup gives 1 PV (the whole disk)
I think you forgot about the FAT formatted EFI system partition on the default install so you will have that besides your PV, so the PV can't use the whole disk.

You could install the way you mention, with separate VGs for different usage. But then, suppose the LV (and VG) for home filled up (they would fill up at the same time). Rather than just expanding the home LV inside a larger VG, you would have to create another PV, add it to the home VG, then expand the home LV. The unallocated space in a VG is only available to LVs in that VG, so if the space you need to expand an LV in VG1 exists in VG2, you can't use it. You have to make that new partiton. 

It's an inefficient use of disk space. I wouldn't do it.

---

### Post by aljames2 on 2023-07-03
Thank you.

I missed that part…that to expand a VG you would need to create and add another PV to it.

For context, my use is with a single 1TB NVMe.  It makes sense to set up the entire SSD with 2 VGs (system & data), maybe a third for /home, all combined spanning the whole disk vs even more smaller VGs.  My other system is all 1 large VG for everything.  This new system I am rethinking the setup I want to use.

---

### Post by MAFoElffen on 2023-07-03
I remember the posts I wrote in that thread and the links I directed to the other posts I wrote. Please pay attention to what TheFu and I preach about "Do not give LVM2, mdadm, ZFS or BTRFS a whole unbound raw disk". Please use partitions to put those into.

I think you missed another of my posts that would be an example to what you are asking and talking about here, where I posted a recipe for LVM2 on LUKS2, finishing the installation with the Installer...
RE: [https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569](https://ubuntuforums.org/showthread.php?t=2488075&p=14148569#post14148569)

If you look at that recipe, I created PV's. Then VG's assigned to specific  PV's. The LV within those VG's. Notice on a start, I don't assign 100% of the VG space. By default I usually assign 80%. TheFu is more conservative, and usually assigns a lot less. The PV's can be partitions on the same disk, or on other / multiple disks. I do this if I am creating a system with LVM2 RAID. It doesn't matter where those partitions are located physically, as long as they can all be mounted back together into the system.

I am a fan of creating more than one VG. That way you "can" isolate and segment a system into pieces for safety, security and maintainability.

I have done this a long time and create a separate boot partition. That is the way it used to have to be. In the past few years, that moved to having the /boot inside of the LVM root LV... But starting with 23.04 in the DEV cycle, this has moved back out of the LVM volume manager in the Installer's install scripts for it. That has come full circle. LOL

---

### Post by Dennis N on 2023-07-03
> **aljames2 said:**
> Thank you.

I missed that part&#8230;that to expand a VG you would need to create and add another PV to it.

For context, my use is with a single 1TB NVMe.  It makes sense to set up the entire SSD with 2 VGs (system & data), maybe a third for /home, all combined spanning the whole disk vs even more smaller VGs.  My other system is all 1 large VG for everything.  This new system I am rethinking the setup I want to use.

Yes, you could do that. But I don't get the advantage of the separate VGs over your original system.  

I use a separate LV for data but other than that, I have all the partitions of the OS in a root LV and mount my data LV to the root file system. I share my data LV between several OS. Since I have 2 disks with several OS installed, the data LV may be on a separate disk from the OS and in a different VG.

---

### Post by Dennis N on 2023-07-03
> **MAFoElffen said:**
>  In the past few years, that moved to having the /boot inside of the LVM root LV... But starting with 23.04 in the DEV cycle, this has moved back out of the LVM volume manager in the Installer's install scripts for it. That has come full circle. LOL

That's interesting. I did see this testing 23.04 trying the "erase and install" + LVM. 

If this is what the future holds, with 4 OS installed as LVM with this requirement, my disk would need 4 boot partitions? Ugh.

FWIW:
I noticed when installing Fedora as LVM in January it also insisted on a separate boot outside the LVM. But a just-installed Debian 12 did not need separate boot with LVM.

---

### Post by aljames2 on 2023-07-03
> **MAFoElffen said:**
> I remember the posts I wrote in that thread and the links I directed to the other posts I wrote. Please pay attention to what TheFu and I preach about "Do not give LVM2, mdadm, ZFS or BTRFS a whole unbound raw disk". Please use partitions to put those into.

I think you missed another of my posts that would be an example to what you are asking and talking about here, where I posted a recipe for LVM2 on LUKS2, finishing the installation with the Installer...

Got it.  I had seen that post and I think it is what got me thinking about other possibilities when setting up LVM.  I think I was just a little unclear on it, better now. The recipe helps!

I understand the point about using LVM within the confines of a partition, and I do this already.  Interestingly, I was reading the Redhat knowledge base on LVM, and they suggest this as well.

---

### Post by aljames2 on 2023-07-03
The new setup will be another KVM host on ubuntu server, with a VM for a Wireguard VPN server & a VM for a Nextcloud server.  The NC data source will be present as read-only.  I haven’t entirely decided where the NC data will live.

---

### Post by MAFoElffen on 2023-07-03
For me, my KVM Hosts and Volume managers, I follow a strategy of having my created KVM Storage Pools on a separate disks or devices. That way if I have to migrate the system because of a disaster, release upgrade or to newer hardware, if I have a copy (backup) of /etc/libvirt/qemu and /etc/libvirt/hooks.... then I can mount / atttach those KVM storage pools back in and restore those two directories ad go from there.

I did that in the past with LVM VG's and now with ZFS pools. Still use the same logic between the two.

I used to keep them on disk as flat storage... But these days, since storage prices have fallen in our favor, for my current (newer) KVM Server, I used RAID pools for those devices, to take advantage of the speed and throughput advantages.

I spin-up and create a lot of VM's for testing purposes, and for play. Most of them are temporary, but about a quarter of them are permanent. I like that they perform better that most than if they were installed on metal. Installations, updates for maintenance, and cloning VM's take no time at all. I am very happy with that decision.

RAID devices in LVM2 and ZFS make things perform very well, and they very are portable.

My KVM Storage pools are for VM Guest image's and then my ISO & OS image libraries. I have scripts that download ISO's and OS images to those storage pools. For example, using wget with an added timestamp injected into the names, to download for the DEV daily ISO's and preinstalled images that I test for QA...

---

### Post by aljames2 on 2023-07-03
> **MAFoElffen said:**
> I did that in the past with LVM VG's and now with ZFS pools. Still use the same logic between the two.

I used to keep them on disk as flat storage... But these days, since storage prices have fallen in our favor, for my current (newer) KVM Server, I used RAID pools for those devices, to take advantage of the speed and throughput advantages.

...

RAID devices in LVM2 and ZFS make things perform very well, and they very are portable.

My KVM Storage pools are for VM Guest image's and then my ISO & OS image libraries. I have scripts that download ISO's and OS images to those storage pools. For example, using wget with an added timestamp injected into the names, to download for the DEV daily ISO's and preinstalled images that I test for QA...

I would like to learn ZFS and I wonder if this setup would be the time to take the plunge.  I'm in no hurry to get the fans spinning, so I could do some research on it.  My other system is all LVMs and my backup scripts are already set up for that.  I do like the snapshotting of LVs, which I use to back up certain aspects of the system.  I understand ZFS is not only a FS but also a volume manager with snapshotting capabilities.

This is what I have schemed out for LVM on the new box:

```

KVM Host  (B550-A-Ryzen5600x)
    |DISK = 1TB Samsung 850 Pro NVMe
    |
    |--> /boot/EFI  (FAT32)
    |
    |--> /boot (ext4)
    |
    |--> PV = /dev/nvme?
    |------> VG = vg-kvm
    |---------> LV = lv-root    /
    |---------> LV = lv-home    /home
    |---------> LV = lv-swap    [SWAP]
    |------> VG = vg-data
    |---------> LV = lv-nc      /data/NC
    |
    |--> PV = /dev/sd?  (500G Samsung SSD)
    |------> VG = vg-imgs1
    |---------> LV = lv-ncvm    /imgs/NC
    |---------> LV = lv-wgvm    /imgs/WG
    |
    |--> PV = /dev/sd?  (250G Samsung SSD)
    |------> VG = vg-imgs2
    |---------> LV = lv-bkvm   /imgs/BK

```

Any ideas on some good Readme's to get started w/ZFS? :)

---

### Post by #&amp;thj^% on 2023-07-03
> **aljames2 said:**
> I would like to learn ZFS and I wonder if this setup would be the time to take the plunge.  I'm in no hurry to get the fans spinning, so I could do some research on it.  

Any ideas on some good Readme's to get started w/ZFS? :)

There is no page that covers an easy read for that. I have some links form other users that might help: [https://www.linuxserver.io/blog/2019-05-14-getting-started-with-zfs-on-linux](https://www.linuxserver.io/blog/2019-05-14-getting-started-with-zfs-on-linux)
And this one is a bit tailored but still has great info: [https://wiki.archlinux.org/title/ZFS#Installation](https://wiki.archlinux.org/title/ZFS#Installation)
And last but not least: [https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/index.html](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/index.html)
And this forum is getting better at helping with zfs systems.
***WARNING It's Addictive :lolflag:

---

### Post by aljames2 on 2023-07-03
Already started reading the OpenZFS site.  Thanks 1fallen for the links.  Do we think zsys is going to survive future releases of Ubuntu?  It reads as though perhaps not.  If I understand, this enables the snapshotting to work.  I'll keep reading on, and start a new thread on ZFS if needed since I've veered off topic in this LVM thread.

Thanks all !!

---

### Post by MAFoElffen on 2023-07-04
[I]This is my ZFS KVM Server to give you "ideas"... Both pools datapool and kpool are KVM storage pools.
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              293M  1.46G       96K  /boot
bpool/BOOT                                         291M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           291M  1.46G      291M  /boot
datapool                                           854G  3.89T      307K  /data
datapool/DATA                                      854G  3.89T      307K  none
datapool/DATA/ubuntu_2cwpns                        854G  3.89T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    383G  3.89T      383G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 461G  3.89T      461G  /data/KVM-VM
kpool                                             1.55T  1.86T      279K  /KVM_Pool
kpool/KVM                                         1.55T  1.86T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.55T  1.86T     1.55T  /KVM_Pool
rpool                                             18.8G   873G       96K  /
rpool/ROOT                                        13.6G   873G       96K  none
rpool/ROOT/ubuntu_2cwpns                          13.6G   873G     6.96G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   873G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   873G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   873G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      6.61G   873G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   873G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  6.38G   873G     6.24G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   873G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    188K   873G      188K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              97.3M   873G     97.3M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             46.0M   873G     46.0M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   228M   873G      228M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   873G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.47M   873G     1.47M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   873G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   873G       96K  /var/www
rpool/USERDATA                                    5.22G   873G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  5.22G   873G     5.22G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.42M   873G     2.42M  /root
mafoelffen@Mikes-B460M:~$ sudo zpool status -v
  pool: bpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:00 with 0 errors on Sun Jun 11 00:24:01 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    bpool                                   ONLINE       0     0     0
      0196ab45-3ee2-894e-b725-39560409109f  ONLINE       0     0     0

errors: No known data errors

  pool: datapool
 state: ONLINE
  scan: scrub repaired 144K in 00:14:36 with 0 errors on Thu Jun 29 03:45:16 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:06:07 with 0 errors on Sun Jun 11 00:30:08 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 00:00:14 with 0 errors on Sun Jun 11 00:24:16 2023
config:

    NAME                                    STATE     READ WRITE CKSUM
    rpool                                   ONLINE       0     0     0
      ae13efaa-d1cf-ec40-86a6-2883f0e07102  ONLINE       0     0     0

errors: No known data errors

```
 I thought zsys was a great idea. The status of 'zsys' in 20.04 was that it was experimental. It being installed by the install scripts wasn't there in 22.04. There were "rumors" that development on it died, that development stopped about 3 years ago... and that was the reason, 

BUT... My interest has picked up again. I see active commits for it for Mantic 23.10: [/I][https://github.com/ubuntu/zsys/tree/master/internal](https://github.com/ubuntu/zsys/tree/master/internal)  It look like there is at least some development again, or at least some actvity with it for Mantic. I will be testing with this in Mantic in this Dev Cycle... I like a challenge. LOL

EDIT: I have also tested this, which I think was inspired by zsys type thoughts, and is an install script for ZFS-On-Root systems that also adds a boot menu with features: [https://github.com/Sithuk/ubuntu-server-zfsbootmenu](https://github.com/Sithuk/ubuntu-server-zfsbootmenu)

---

### Post by aljames2 on 2023-07-07
> **MAFoElffen said:**
> EDIT: I have also tested this, which I think was inspired by zsys type thoughts, and is an install script for ZFS-On-Root systems that also adds a boot menu with features: [https://github.com/Sithuk/ubuntu-server-zfsbootmenu](https://github.com/Sithuk/ubuntu-server-zfsbootmenu)

I think I will give the script a try this weekend.  I have seen other scripts as well, it seems to help automate the installation process somewhat.  

The manual instructions at OpenZFS apply to desktop version only for root installs.  I was going to use their manual method, but I prefer to install Ubuntu Server instead.

Looks like I would have a similar setup on mine, as you have shown MAFoElffen.  I’m curious why these boot installations show /var & /usr in the rpool list.  Why not /etc or /opt etc.  I guess those all just stay lumped under /.  Just an oddity I’ve noticed, i’m sure there must be a good reason for it.

---

### Post by MAFoElffen on 2023-07-07
You can certainly add more granularity or tweak it to how you want... Or change to how you want. I just follow usual rules of thumb and guidelines.

For a rule of thumb explanation, here is a short list based on Linux Directory structure of what and where things are usually used for... Based on what is on my server (listed above):
```

/ - Stores all the directories in Linux. The top of the tree.
/boot - Stores the important files needs by the bootloader, and the initramfs (initial ram file system) files.
/dev - Linux treats everything as a files system. This stores all virtual files representing the device files.
/etc - Stores all the core configuration files used for system-wide changes
/lib->usr/lib - Stores all the shared libraries. The shared binaries used by the executibles from bin, sbin, etc.
/lib32->usr/lib32
/lib64->usr/lib64
/libx32->usr/libx32
/opt - Stores optional software packages. (Third party repo's and such) I used this more back in Solaris and OpenSolaris days.
/srv - Stores service data. Used more with Apache web server for website files. www, ftp & cvs.
/tmp - Stores temporary files. Deleted at boot up.
/usr - Stores most of the files, libraries, programs, and system utilities. Think as User binaries and read-only data.
/var - Stores system-generated variable files, and it includes logs, caches, and spool files. Persistant.

/proc - Stores information about processes and kernel parameters.
/sys - Stores information about the various system components and drivers. Like /proc but in different format.
/run - Stores application state files. Logs system information since boot time, about the daemons that are running, logged-in users, and more.

/cdrom - leagacy mount point for optical storage devices.
/media - Usually the temporary mount points for removable storage devices. Folders are added at automunt, and deletes on removal 
/mnt - Used for temporary mounts. Folder not created automatically here.

/bin->usr/bin - Stores system commands and other executable programs.
/sbin->usr/sbin - Stores system commands and other executable programs.

/home - individual user directories. Includes user settings.
/root - the root user directory. Includes root user settings.

My Network shares and shared data: (Specific to mine... Follows smb shares administrator guidelines)
/data
/data2
/KVM_Pool
/nfs/exports/ <-- Usual rule of thumb recommendation from RedHat for nfs shares...

Other:
/snap - Mount point for Snaps loop devices.
/lost+found &#8212; Recovered Files from ext files systems (I don't use ext4 on mine...)
/selinux &#8212; SELinux Virtual File System containing files if SElinux is used by system. (Not used by Ubuntu)

```

---

