---
title: "Installing LVM"
date: 2023-02-16
forum: General Help
---

### Post by Quarkrad on 2023-02-16
I'm thinking of moving to lvm on a new hd install.  Although this is a Desktop machine I can see how having **/** and **/home** on separate logical volumes, and then creating other logical volumes for other projects (e.g. vm machines), there is an advantage that if I ever needed to increase **/** (as I have had to do in the past, with pain) the lvm environment would give me distinctive advantages. I tried to test all this in a VM but came unstuck, the (ubuntu) installer only gives the option to lvm the whole disc so when it comes to shrinking (first the file system and then the logical volume) I don't think you can do this on a vm as I understand you need the liveCD environment to act on the vm.  (My understanding of what you can and cannot do with a vm is limited!).  I'm not sure how to implement lvm on a new HD.  Do you somehow create the lvm environment with separate logical volumes first and then install ubuntu into those logical volumes (e.g. one for **/** and one for **/home**).  Or do you install ubuntu and the whole HD as one big logical volume (using the lvm option) and then using a liveDC environment shrink the file system and logical volumes?

---

### Post by Dennis N on 2023-02-16
>  I'm not sure how to implement lvm on a new HD.
You are on the right track. The "advanced features" button has a "use LVM" option, but you don't want to use that, as it uses the entire disk for the VG and LV of the OS. You create the LVM structure before starting the installer - partition table, partitions, volume group, and logical volume(s). That way, you can specify the size of the partitions and logical volumes.  
Example of initial partitioning using gparted from live media. Note the lvm partition (partition 2) is formatted as lvm2-pv in gparted.
```
Disk /dev/nvme0n1: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name     Flags
 1      1049kB  106MB  105MB   fat32                 boot, esp
 2      106MB   787GB  786GB                         lvm

```
Then, you use terminal in live media to work with the lvm partition. Create a volume group containing it to house the logical volume(s) needed for your OS. Create the LVs needed for the OS and format them ext4. The LVs need not fill the entire VG. Make them only as large as necessary. The unused part is for expanding or creating new logical volumes.

Then you can start the installer and use the "something else" option. You can select the LVs like you select partitions in a regular install - they appear above the partitions in the partitions display - and then complete the install.

---

### Post by dragonfly41 on 2023-02-16
I am reading how to set up virtual desktops in the cloud for remote training.

I thought about LVM (there ae experenced users here in forum who can better advise you rather than me).
Two tutorials are bookmarked here.

[https://linuxconfig.org/ubuntu-22-04-enable-full-disk-encryption](https://linuxconfig.org/ubuntu-22-04-enable-full-disk-encryption)

[https://jumpcloud.com/blog/how-to-enable-full-disk-encryption-on-an-ubuntu-20-04-desktop](https://jumpcloud.com/blog/how-to-enable-full-disk-encryption-on-an-ubuntu-20-04-desktop)


But since I want to open/shut down unused Virtual Desktops I am puzzling about how to approach this in a PaaS account.
The instances will be in Google Cloud Platform and others.

---

### Post by Quarkrad on 2023-02-16
Dennis N   thank you, that explains a lot.  Although I have installed ubuntu many times using the *something else* option I have never specified a *EFI System Partition* - this has always been created for me by the installer.  If I use gparted to create the 1st partition in your example - when I come to installing ubuntu will the installer automatically use this partition for the *EFI System Partition* because of the flags set?  So ... for a 1T HD could you use gparted to create the following:

1.  105mb     fat32    boot, esp
2.  50GB       ext4      lvm
3.  150GB     ext4      lvm

When using the installer point **/** to 2. and **/home** to 3.

What I'm not sure about is the volume group.  Do you have to create this at some point?  Also .... is it the case that just by setting the lvm flags for, say two partitions via gparted, a whole lvm environment is created and you can use the multitude of lvm terminal commands to manage it?

Apologies for these questions - I have read some data on lvm and assumed (probably incorrectly) it was a 'thing' you installed.  I'm beginning to think it is not a 'thing' as such (like installing an application but lvm works at a system/architecture level).

---

### Post by TheFu on 2023-02-16
LVM2 is the name of all the different parts.  PVs, VGs, LVs are where we do the work.  Really, once the PVs and VGs are setup on a disk, it is unlikely you'll touch those again unless you want to move a PV to a larger disk or you want to create a mirror (which is done at the VG and LV level).  

For simplicity, think of an LV as a partition - a really smart partition that can be extended as needed, when needed ... or mirrored or split (if it was a mirror).  This create-mirror, split-mirror is how we move LVs to different physical devices.  Very powerful.  I've moved an entire PV on a running, active, system using 1 command before.
See the attached image to see the relationships between PVs, VGs, and LVs. Hope that helps.  I tried to keep it simple. That image shows an encrypted LUKS container, but that can be completely removed/ignored.  A PV is usually setup on a full partition.  

**The Ubuntu installers all suck for storage setup.**  As for how to install with custom LVM setups. , after I boot into the installer, I install ssh and pull a little 50 line script over to customize sizes and types for my desired disk layout.  Once that is handled, I run 'sudo vgchange -ay', choose "do something else" in the storage menu and just connect the core areas ... /, /boot, /efi, /home, /var, and swap ... for the installer to use.  The installation won't continue if the installer doesn't like what I've connected.  Spent 30 minutes 1 day just fighting with the installer to get what I wanted acceptable to it.  Sometimes it was as simple as allowing the installer to format an LV that didn't need to be formatted again - whatever.

My script is ugly, but it is just lots of 'sgdisk', pvcreate, vgcreate, lvcreate, mkfs, mkswap, and e2label commands. It has to be tweaked every time.  My attempts at coming up with a data file format for a more generic version failed ... well, it was becoming overly complex. I'd already wasted far too much time and knew that just setting some environment variables would work.  It doesn't have **any** error checking or validations, so not safe for anyone else to use.

I always do a minimal install to keep cruft out as much as possible, typically, just ssh and nothing else.  I seldom want the all the programs that Desktop and Server people seem to get with typical installs.  I can see where someone new would like to have stuff already loaded - that ain't me.

BTW, when I first started using LVM, I just checked the LVM box and let it go.  After a few years, I knew the issues that caused and wanted to avoid them going forward.  Shrinking an LV is relatively easy just after the install but it can't be active/mounted, so do it ASAP, before anything else.  Would be great if the Ubuntu installer let us control the sizes of LVs in the use whole drive+LVM choice.  There's no way I'd want / to be 200GB!

Adding more LVs is trivial and increasing the size of an LV is trivial tool - takes just a few seconds and the file system doesn't even need to be off-line (for lvextend).

Of course, you could check out ZFS too, if you want to skip LVM completely.  Eventually, ZFS will become the default volume management on all our systems and not just for data.  Today, there seem to be some OS upgrade issues with ZFS involved for the core OS, but hopefully, that will become cleaner.  For my servers, I'm still using LVM, but just started playing with ZFS on a Mint desktop.  I'd used ZFS on Solaris about 15 yrs ago, but haven't used it for anything besides toy systems under Linux.

---

### Post by Dennis N on 2023-02-16
The installer will find the EFI system partion and mount it at /boot/efi. You don't need to specify the mount point.

You really need only one lvm partition (called a physical volume) and one volume group, but you will have multiple logical volumes. You have to use the terminal to make a VG using the **vgcreate** command, and then the LVs with the **lvcreate** command before starting the installer. 

example: sudo vgcreate vg_01 /dev/nvme0n1p2
example: sudo lvcreate --size 30G -n ubuntu vg_01

You can expand the VG later by making and adding another partition to it if you run out of room.

You make a logical volume for / and optionally another for ~/. But, my practice is to leave home folder in the root partition and create a 2nd logical volume just for my files (data). This scheme is shown below. (p3 is explained in last paragraph)

```
dmn@Kayleigh:~$ lsblk -o name,label,fstype,mountpoint
NAME                 LABEL        FSTYPE      MOUNTPOINT

nvme0n1                                       
&#9500;&#9472;nvme0n1p1                       vfat        /boot/efi
&#9500;&#9472;nvme0n1p2                       LVM2_member 
&#9474; &#9500;&#9472;vg_01-Common     Common-Files ext4        /mnt/Common-Files
&#9474; &#9492;&#9472;vg_01-ubuntu     Ubuntu       ext4        /
&#9492;&#9472;nvme0n1p3          Manjaro      ext4        

```

Before any installing, vg_01 is created from p2

Then, two logical volumes, named Common and ubuntu, were created in vg_01 (Each LV requires a name when it's created). You point the installer to a specific LV, not a partition. ubuntu is the LV that I tell the installer to use for / when installing. Common is for my data and I set up it's mounting in fstab after installing the OS.

On this computer, I have installed Manjaro too, but it had to go on a regular partition (p3) outside the lvm partition because their current installer (called Calamares) can't detect logical volumes. Manaro still shares the Common LV as a data partition.

There are many articles on the usage of the lvm commands you can find with google.

Read this for inspiration:
[https://www.linuxjournal.com/content/lvm-demystified](https://www.linuxjournal.com/content/lvm-demystified)

---

### Post by aljames2 on 2023-02-16
I also use LVM.  My structure is below.  What I like about LVM is it has snapshotting capabilities. You can create snapshots of logical volumes, or even specific directories within an LV.  I use this for creating versioned backups.  This is my KVM host and it runs on my nvme 1TB stick.  My sda is an extra internal SSD, & my sdb is an external USB connected spinning disk.  I tend to encrypt portable storage.

I do as already suggested, which is to use the installer USB 'try ubuntu' to gain access to the GParted utility and a command line.  Then during the installation, select 'something else' in the installer and match up your LVs (which you have already created) with their respective mountpoints.  Of course, if your machine is booting in UEFI then you will also need that EFI (vfat) partition which you can also create using the GParted utility.  So basically, you are prepping your storage device with the partition scheme you want before running the installer.

```

NAME           SIZE FSTYPE      MOUNTPOINT

sda          465.8G             
sdb            1.8T crypto_LUKS 
nvme0n1      931.5G             
&#9500;&#9472;nvme0n1p1    512M vfat        /boot/efi
&#9500;&#9472;nvme0n1p2    700M ext4        /boot
&#9492;&#9472;nvme0n1p3  930.3G LVM2_member 
  &#9500;&#9472;LVG-swap     6G swap        [SWAP]
  &#9500;&#9472;LVG-root    60G ext4        /
  &#9500;&#9472;LVG-home    30G ext4        /home
  &#9492;&#9472;LVG-VMs    150G ext4        /media/data

```

---

### Post by Quarkrad on 2023-02-18
Thank you all.  Successfully got lvm working on spare small hd and also, now in a vm on my main machine.  Will have a play before implementing on my new hd.

---

