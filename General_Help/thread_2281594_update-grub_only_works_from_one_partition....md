---
title: "update-grub only works from one partition..."
date: 2015-06-08
forum: General Help
---

### Post by timgood on 2015-06-08
I have Ubuntu-Gnome installed on a Btrfs partition and Kubuntu installed on an extended partition (see screenshot).  If I run update-grub from the Btrfs partition, both OS's are updated. But if I do the same from the Kubuntu partition, although update-grub runs and no errors are detected, Grub is not updated and the old kernel will boot rather than the new one. Have I missed something?

 [ATTACH=CONFIG]262484[/ATTACH]

---

### Post by sudodus on 2015-06-08
I think update-grub is independent of the current directory or partition.

I think you have another problem:

The latest installed system grabs the boot, because it installs the bootloader. So when you update-grub in the other system, its grub menu will not be used. However, you can activate it by installing grub from that system

```
sudo grub-install /dev/sdx
```

where **x** is the drive letter of the drive that is booted by the BIOS/UEFI. Normally it is **a**, so

```
sudo grub-install /dev/sda
```

If you have grub in an unusual place you need the boot option --boot-directory

```
       --boot-directory=DIR
              install GRUB images under the directory DIR/grub instead of the /boot/grub directory
```

---

### Post by timgood on 2015-06-08
Thanks. Will give it a go.

---

### Post by grahammechanical on 2015-06-08
I have not installed Ubuntu on a btrfs partition for more than a year. When I was experimenting with btrfs I noticed that Grub does not detect Linux kernels on btrfs partitions.

If I ran update-grub from Ubuntu on a btrfs partition it would detect the kernels on that partition and the kernels on Ext4 partitions but it would not detect Linux kernels on other btrfs partitions. If I ran update-grub from Ubuntu on a Ext4 partition it would not detect Linux kernels on any btrfs partition.

Has the situation changed?

Regards.

---

### Post by Keith_Helms on 2015-06-08
> **timgood said:**
> I have Ubuntu-Gnome installed on a Btrfs partition and Kubuntu installed on an extended partition (see screenshot).  If I run update-grub from the Btrfs partition, both OS's are updated. But if I do the same from the Kubuntu partition, although update-grub runs and no errors are detected, Grub is not updated and the old kernel will boot rather than the new one. Have I missed something?

 [ATTACH=CONFIG]262484[/ATTACH]

You haven't missed anything.  Each 'buntu install also installs Grub, which points the hard drive to that install partition to get the grub menu.  At install time, the grub in that partition picks up the other OSes/kernels installed on the drive and adds them to its boot menu.  I'd say you installed Ubuntu Gnome last and it is where the drive looks for the grub menu.  When you update the Kubuntu system and get a new kernel, it will rebuild the grub menu in its partition, but that is not the one that the system is looking at at boot time.

Bottom line, each 'buntu OS has its own grub menu, but the hard drive can only point to one of those.  If you add or remove kernels in the "other" OS(es), then you will have to manually run update-grub in the OS that the hard drive is actually pointing to.  Running grub-install in that other OS will just give you the same problem in reverse.

**grub-install** - points the hard drive to the grub menu in the OS you run it from.
**update-grub **- rebuilds the OS/kernel list for the grub menu under the current OS, which is _*not necessarily*_ the one the hard drive is looking at.

FYI - I've noticed that some maintenance updates to grub also cause grub-install to be run which can cause your system to suddenly be using a different partition's grub menu than before.  Keep an eye out for that when you have 2 or more systems installed on a drive.

---

### Post by oldfred on 2015-06-08
Grub remembers which drive you originally installed into and reinstalls to that drive on major updates. So with two grubs you can have issues. Or if installed to a different drive originally, you get a half updated grub that gives issues.

You can uncheck all install locations or install to a partition as a throw away for a second install. Then only your main working install is in control of MBR.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If a second install you can choose partition or you can uncheck all options and it will remove the reinstall location. Double check by re-running command on which drive is install drive.

---

