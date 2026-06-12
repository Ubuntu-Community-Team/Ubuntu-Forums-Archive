---
title: "Gparted showing changed driver order"
date: 2015-06-10
forum: General Help
---

### Post by bookie2 on 2015-06-10
Hi guys[IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]
I have a system where I have a SSD drive that is formated to / root, /home and swap...
I have four 2TB drives in raid5
And the last 1TB drive as a driver for my virtual machines...

When I originally installed the system I had nothing on any drive, so I could set up the system as follows:

/dev/sda SSD drive
/dev/sdb 2TB raid
/dev/sdc 2TB raid
/dev/sdd 2TB raid
/dev/sde 2TB raid
/dev/sdf1TB virtual machines

I swap between distros according to who works best at the time...
I don't have the luxury of choosing something I like when running a business...
I love Ubuntu and Debian because of the obvious...Debian is a great sound distro and Ubuntu is a great distro that is based on Debian...

I use my raid5 system for my customer images created by clonezilla...

I had to move from Debian because of problems with the latest release Debian Jessie...
I could not get it to work with Jessie on my hardware....?!
I then tested Ubuntu Gnome, Xubuntu, and Ubuntu....all of them work straight out of the box with the latest version of clonezilla....so that was settled I move back to Ubuntu for my Server....[IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]

When reinstalling on the SSD drive I removed the others for safety and just installed on the SSD first...

I then added my raid5 array no problems and finally the drive for my virtual machines....no problems so I thought...

After mounting and adding everything to fstab I rebooted...

When I check gparted the order isn't as it was when I originally installed Debian...now I have:

/dev/sda 2TB drive
/dev/sdb 1TB drive
/dev/sdc SSD
/dev/sdd 2TB drive
/dev/sde 2TB drive
/dev/sdf 2TB drive

I don't know what causes this because the drives are in order in the machine...checked....double checked....;)

But that isn't the whole problem...if it can be called a problem....
Sometimes when I boot into ubuntu I get error mounting a drive do I want to skip it and continue...I skip it and then find out that the drive is listed in gparted as /dev/sdf 1TB. Because of this I have a mount point that is wrong in fstab and /dev/sdb has been labelled as the virtual machine drive and that of course is wrong...

I have installed Smart ctl and, gsmartcontrol to test the drives...as soon as I go to gsmart control I see and error for my 1TB drive but it isn't noted as serious just indiscriminate....

I am about to change the drive to see what happens - but just wondered why drive the drive order isn't how it was originally...

when installing now I added the SSD first, then the raid5 array, and finally the virtual machine drive...but I still get the order as above?

Is there a way to set this so it doesn't change?

I will post after adding the new drive...

Thanks!

---

### Post by Bucky Ball on 2015-06-10
This is from left field, but have you tried changing the SATA connectors around on the motherboard? The motherboard SATA sockets should be numbered 1-4 or how ever many you have. Just a thought. Whatever is plugged into SATA port 1 is possibly being picked up as sda. Or, whichever drive you are booting from might be getting picked up as sda then the rest in the order they are physically plugged in.

---

### Post by bab1 on 2015-06-10
The /dev/sdX designation is set by the kernel in the order the device is enumerated (found).  It should not be used in the fstab to ID the partition to be mounted.  You should use the UUID of  the partition.  This is clearly described at the top of the fstab file```

# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).

```

It does not matter where you physically mount the drive or what header you use on the mobo at all.  For example I mount a separate partition for /home like this in my fstab```
UUID=0cb1063b-d6ae-48ba-af5d-33ee8cb7fb39 /home           ext4    defaults        0       2
```

To find the UUID I use this incantation```

sudo blkid -c /dev/null -o list

```

---

### Post by bookie2 on 2015-06-10
Hi guys!
OK!
Bucky Ball:
I have them in the same order as they were in the beginning and the bios shows them in the right order...

bab1:
I have to admit I didn't read that text in fstab....lol

As it is the changing of the drive didn't change the problem...
The first reboot I everything was OK and the second it had been as above:
```

/dev/ sdb1 (had become a raid drive and the mount point is /VirtualMachines..

```

This is the original fstab
```


  # /etc/fstab: static file system information.
  #
  # Use 'blkid' to print the universally unique identifier for a
  # device; this may be used with UUID= as a more robust way to name devices
  # that works even if disks are added and removed. See fstab(5).
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  # / was on /dev/sda1 during installation
  UUID=faa5b340-4cb8-40d1-a0ec-c2ef260bd038 /               ext4    errors=remount-ro 0       1
  # /VirtualMachines was on /dev/sdf1 during installation
  UUID=3024927b-3217-43c3-90cd-979781f1d2ba /VirtualMachines ext4    defaults        0       2
  # /home was on /dev/sda2 during installation
  UUID=e636cd19-104d-407a-be8e-f910ecd21b67 /home           ext4    defaults        0       2
  # /home/partimag was on /dev/md0 during installation
  UUID=6d98f42c-7029-4376-8e8a-f9ee8659b1aa /home/partimag  ext4    defaults        0       2
  # swap was on /dev/sda3 during installation

  UUID=c541805c-c861-4b7a-a30e-cc453a0c0c7f none            swap    sw              0       0
  [FONT=&amp]/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       [/FONT]


```

I will add the original drives and then check what your command gives me...

```

sudo blkid -c /dev/null -o list

```

In theory the fstab should be as original...?
After editing fstab...do I need to do anything else?

---

### Post by bab1 on 2015-06-10
For the new mounts to be used you can just issue this command```
sudo mount -a
```...or reboot the machine.

After that the mounting of the partitions will always be via the UUID's at boot up time.

[COLOR="#0000FF"]Edit:  The bkkid command is used to determine what the UUID is for the partition that you are trying to mount.  You should check the **before** editing the fstab file.  The fstab should be as it needs to be for your machine to function correctly.  No two machines are the same.[/COLOR]

---

### Post by bookie2 on 2015-06-10
Hi again!
OK! 
Thanks for that...will post when I have had the time to check everything....;)

---

### Post by bookie2 on 2015-06-10
Hi again!

Just to check a few things....lol

This is the result of your command


```

martyn@DN-Server:~$ sudo blkid -c /dev/null -o list
[sudo] password for martyn: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  linux_raid_member DN-Server:0 (in use) 5b63984e-bfae-d616-be4b-2dddce872e97
/dev/sdb1  ext4             /              2ba2477a-39ff-44f2-80d7-e9f0c7008a42
/dev/sdb2  ext4             /home          8ca095f7-dc90-46e8-b4db-bffa86ceebbb
/dev/sdb3  swap             <swap>         ccafe4c3-fa29-4efd-b7ef-7be479485fdb
/dev/sdc1  linux_raid_member DN-Server:0 (in use) 5b63984e-bfae-d616-be4b-2dddce872e97
/dev/sdd1  linux_raid_member DN-Server:0 (in use) 5b63984e-bfae-d616-be4b-2dddce872e97
/dev/sde1  linux_raid_member DN-Server:0 (in use) 5b63984e-bfae-d616-be4b-2dddce872e97
/dev/md0   ext4             /home/partimag 6d98f42c-7029-4376-8e8a-f9ee8659b1aa
martyn@DN-Server:~$ 



This is my fstab at the moment:


```

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2ba2477a-39ff-44f2-80d7-e9f0c7008a42 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=8ca095f7-dc90-46e8-b4db-bffa86ceebbb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=ccafe4c3-fa29-4efd-b7ef-7be479485fdb none            swap    sw              0       0
/dev/md0  /home/partimag                                  ext4    defaults        0       2
/dev/sdb1  /VirtualMachines                               ext4    defaults        0       2


```


Your command doesn't show UUID right order for SSD drive+
In the original fstab I only had a UUID for the /dev/md0...do I need to add all the drives as your command shows?

I will add that my 1TB drive isn't installed at the moment...changing it to original again....lol

---

### Post by bookie2 on 2015-06-10
Hi guys!
I just made the two entries as it was in the beginning to fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2ba2477a-39ff-44f2-80d7-e9f0c7008a42 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=8ca095f7-dc90-46e8-b4db-bffa86ceebbb /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=ccafe4c3-fa29-4efd-b7ef-7be479485fdb none            swap    sw              0       0
UUID=6d98f42c-7029-4376-8e8a-f9ee8659b1aa /home/partimag  ext4    defaults        0       2
UUID=3024927b-3217-43c3-90cd-979781f1d2ba /VirtualMachines ext4    defaults        0       2


```

Now my gparted is showing the order as it was from the beginning....

Sorry, many thanks for teaching me more about UUID....I am sold now...

---

### Post by Bucky Ball on 2015-06-10
Great news and glad you like it. :)

Please mark the thread as solved to help others by following the second link in my signature.

If you enjoy the learning curve you should fit right in!

---

