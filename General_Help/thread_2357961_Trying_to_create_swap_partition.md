---
title: "Trying to create swap partition"
date: 2017-04-08
forum: General Help
---

### Post by superkid333 on 2017-04-08
I need help creating a swap partition as a logical partition within my extended ubuntu partition. I had it there, then I did something which removed it. The 16GB is still listed as unallocated, but Gparted gives me an error when I try to create the partition. 

Here is a screenshot. I have been searching for hours, eventually a mod suggested I make my own post. Thanks ahead of time for the help. 
[https://drive.google.com/open?id=0BxbpOiUj-3Lic3VXSXFTVE05dFk](https://drive.google.com/open?id=0BxbpOiUj-3Lic3VXSXFTVE05dFk)
[IMG]https://drive.google.com/open?id=0BxbpOiUj-3Lic3VXSXFTVE05dFk[/IMG]

---

### Post by Bucky Ball on 2017-04-08
Please confirm.

You are right clicking the unallocated space and selecting 'New'.
You are selecting 'Create as: Logical' and 'Filesystem: linux-swap'.

What is happening when you then try to create the space. You say it won't work, but give not details about how it's not working. Please be specific with what happens, where it stops, any errors you are getting.

PS: Unless you hibernate, you do not need anything like 16Gb /swap. 2Gb is fine. Old-school rule of thumb puts /swap at the end of the drive, but doesn't matter. Is fine where it is, or will be.

Once you have created /swap you will need to add it to the /etc/fstab file. Let us know if you need help with that.

---

### Post by Perfect Storm on 2017-04-08
Moved to General Help

---

### Post by superkid333 on 2017-04-08
> **Bucky Ball said:**
> Please confirm.

You are right clicking the unallocated space and selecting 'New'.
You are selecting 'Create as: Logical' and 'Filesystem: linux-swap'.

What is happening when you then try to create the space. You say it won't work, but give not details about how it's not working. Please be specific with what happens, where it stops, any errors you are getting.

PS: Unless you hibernate, you do not need anything like 16Gb /swap. 2Gb is fine. Old-school rule of thumb puts /swap at the end of the drive, but doesn't matter. Is fine where it is, or will be.

Once you have created /swap you will need to add it to the /etc/fstab file. Let us know if you need help with that.

Thanks for the help. I do hibernate, so I'm comfortable with the 16 GB. 

My /swap was originally at the end of the drive, but during some process it was moved to the middle. Anyway, I go through the process of selecting the 16gb unallocated in the Extended drive, click "new" partition. Ensure that it is logical (not primary), and choose swap as the file system. 
Here is a screen shot of that:
[https://drive.google.com/open?id=0BxbpOiUj-3LiR2h1clBUeHBzckE](https://drive.google.com/open?id=0BxbpOiUj-3LiR2h1clBUeHBzckE)

When I do that, and then begin to save those changes, that is when I get the error. Gparted says "Unable to satisfy all the constrains on the partition"
Here is a screen shot of that:
[https://drive.google.com/open?id=0BxbpOiUj-3LiWnBOYzVsSE5FT00](https://drive.google.com/open?id=0BxbpOiUj-3LiWnBOYzVsSE5FT00)

Here is what fdisk -l produces so you know:
```

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xfc98230b


Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1  *          2048    1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2          1026048   13608959  12582912     6G 27 Hidden NTFS WinRE
/dev/sda3         13608960  643571711 629962752 300.4G  7 HPFS/NTFS/exFAT
/dev/sda4       1111177215 1953523711 842346497 401.7G  f W95 Ext'd (LBA)
/dev/sda5       1111177216 1151176703  39999488  19.1G 83 Linux
/dev/sda6       1183176704 1953523711 770347008 367.3G 83 Linux


Partition 4 does not start on physical sector boundary.

```

My blkid produces this output:
```

/dev/sda1: LABEL="System" UUID="F6160B38160AF8FF" TYPE="ntfs" PARTUUID="fc98230b-01"
/dev/sda2: LABEL="Recovery" UUID="22BA0C63BA0C35B7" TYPE="ntfs" PARTUUID="fc98230b-02"
/dev/sda3: LABEL="NeoSeaDrive" UUID="01D2A7E762F5DE10" TYPE="ntfs" PARTUUID="fc98230b-03"
/dev/sda5: UUID="8ff45c43-a6fb-4361-8e8d-8480b136fa4c" TYPE="ext4" PARTUUID="fc98230b-05"
/dev/sda6: UUID="c396cbc8-d9b6-4f69-b001-60fc0d46980f" TYPE="ext4" PARTUUID="fc98230b-06"

```

And my fstab currently looks like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=8ff45c43-a6fb-4361-8e8d-8480b136fa4c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9acc3489-4a18-4b9b-971d-116cd6c06f57 none            swap    sw              0       0
UUID=c396cbc8-d9b6-4f69-b001-60fc0d46980f /home ext4 defaults 0 2

```

Based on that information, I can tell that my swap had a UUID at some point, and now the mount points have changed. My /dev/sda4 is the entire extended primary partition for Ubuntu, or "/" . Logical partitions are /dev/sda5 is the /boot and /dev/sda6 is the /home. 

All this started because I wanted to increase the /home partition, which required increasing the entire extended primary partition. This required I shrink my Windows partition (done using Minipartition, a windows tool). So I have this huge 230+ GB unallocated space sitting outside my linux partition that I would eventually like to use. Anyway, in an attempt to do all of this, I ran into trouble, used a linux program called "fixparts" to change my partition table, and ended up here. 

Again any help is appreciated. Thanks!

---

### Post by Keith_Helms on 2017-04-08
From the screenshots, it looks like you've selected a big 223gb unused area to put the swap file in, then you told gparted to make it 16gb, leave 1gb free before it and 0gb free after it.   Those numbers don't match the size of the unused area, so gparted doesn't know what to do.  Normally when you set a partition size in gparted, it will add any unused space to the free amount following it.   Did you manually change that number to zero?

Anyway, I think that's what your problem is.  The numbers don't add up.

---

### Post by superkid333 on 2017-04-08
Hi,

No, I did not select the big 223GB unallocated area to put the swap. I have selected the 16GB unallocated which is within the primary/extended partition. Although in the screen shot, you can see the larger unallocated partition, outside the extended partition. It is not selected. However I appreciate your input. 

So, any guesses as to why I am getting this error still?

---

### Post by kansasnoob on 2017-04-08
Are you working from a live DVD/USB? All partitions within the extended partition must be unmounted.

---

### Post by Keith_Helms on 2017-04-09
> **superkid333 said:**
> Hi,

No, I did not select the big 223GB unallocated area to put the swap. I have selected the 16GB unallocated which is within the primary/extended partition. Although in the screen shot, you can see the larger unallocated partition, outside the extended partition. It is not selected. However I appreciate your input. 

So, any guesses as to why I am getting this error still?

Okay.  The 2nd screen shot looked like the big area was selected.  On the first shot, you have a 15624mb area that you are trying to create a 15624mb swap partition in with 1mb free space preceding it.  Try changing that 1 to 0 and then click on add.  If that's not it, try reducing the 15624 by a few mb.  Sometimes gparted gets fussy about partition alignment.

---

### Post by superkid333 on 2017-04-09
> **kansasnoob said:**
> Are you working from a live DVD/USB? All partitions within the extended partition must be unmounted.

I am not on the USB/DVD Live. Damn, so I guess I have to do it from there. I have a Kali live distro, which should have gparted on there. Let me check. 

And Keith_Helms - yeah I have heard that too, it can be fussy about the exact size. I'll try reducing it. But I think I'm a noob and I'm just trying to create a partition while it is mounted.

---

### Post by SeijiSensei on 2017-04-09
First, there's a conflict in UUIDs.  The one for the swap partition on /dev/sda5 in /etc/fstab does not match the one reported for that partition by "fdisk -l".

Let's try using the command line.  

First, use "sudo fdisk /dev/sda" and change the "type" of partition 5 to 82 (Linux swap) with the "t" command.  Write the changes to the drive with "w".   You may need to reboot at this point. Then run
```
sudo mkswap /dev/sda5
```

Now use "sudo fdisk -l" to see what UUID has been assigned to the swap partition.  Edit /etc/fstab accordingly.

Finally run "sudo swapon" then "top", and see if it reports that swap is active.

---

### Post by superkid333 on 2017-04-10
> **SeijiSensei said:**
> First, there's a conflict in UUIDs. The one for the swap partition on /dev/sda5 in /etc/fstab does not match the one reported for that partition by "fdisk -l".

Let's try using the command line. 

First, use "sudo fdisk /dev/sda" and change the "type" of partition 5 to 82 (Linux swap) with the "t" command. Write the changes to the drive with "w". You may need to reboot at this point. Then run
```
sudo mkswap /dev/sda5
```

Now use "sudo fdisk -l" to see what UUID has been assigned to the swap partition. Edit /etc/fstab accordingly.

Finally run "sudo swapon" then "top", and see if it reports that swap is active.

Hi - I'm a bit worried that if I overwrite my /dev/sda5, that I'll lose my root / since that is currently mapped to /dev/sda5. I agree there is something not matching in my fstab. I'm not really certain what to update in my fstab though. I know how to use nano (mostly) in order to update it.

Is the issue that I am actively Ubuntu while trying to rename those partitions? I don't have a live USB that works, I have to go buy a new one.

---

### Post by Bucky Ball on 2017-04-10
If you are trying to change the / partition in any way while you are running the OS, yes, that is the problem. You need to create boot media, 'Try Ubuntu' and use Gparted. The partitions need to be unmounted to do anything with them. / can not be unmounted if it is running the OS.

---

### Post by SeijiSensei on 2017-04-10
> **superkid333 said:**
> Hi - I'm a bit worried that if I overwrite my /dev/sda5, that I'll lose my root / since that is currently mapped to /dev/sda5.
I'm just going by what I saw in the information you posted above:
> # swap was on /dev/sda5 during installation
and
> /dev/sda5       1111177216 1151176703  39999488  19.1G 83 Linux
So did you use the former swap partition to be the new filesystem root?  19 GB isn't an unreasonable size for a Linux filesystem, but since it was the smallest partition, and had been used as swap before, then I was guessing it was where you wanted swap to be.  If it's actually mounted as "/" then, yes, you should leave it alone.

What is the 367 GB /dev/sda6 used for?  Can you shrink it and reallocate the freed-up space to swap?

Otherwise you should just [create a swap file]("https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F").

---

### Post by superkid333 on 2017-04-11
Hi again,

I'm sorry, I should have said that 19GB /dev/sda5 is /boot, not /
The larger 367 /dev/sda6 is my /home. 

I looked into a swap file, however from what I read on the Swap FAQ for Ubuntu, it doesn't currently support it
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F)

I have USB media and I will attempt to run Ubuntu Live and then use gparted on that and see what happens. :) Be back in like 20 minutes (I hope)

---

### Post by kansasnoob on 2017-04-11
> **superkid333 said:**
> Hi - **[COLOR="#FF0000"]I'm a bit worried that if I overwrite my /dev/sda5,[/COLOR]** that I'll lose my root / since that is currently mapped to /dev/sda5. I agree there is something not matching in my fstab. I'm not really certain what to update in my fstab though. I know how to use nano (mostly) in order to update it.

Is the issue that I am actively Ubuntu while trying to rename those partitions? I don't have a live USB that works, I have to go buy a new one.

You were wise to worry! When you are done creating a new SWAP partition with Gparted please post the output of:

```
sudo parted -l
```

That will provide the new SWAP device designation, eg; /dev/sda7. Then we'll check the prior UUID's:

```
cat /etc/fstab | grep swap
```

```
cat /etc/initramfs-tools/conf.d/resume
```

Then we can use mkswap to correct the UUID.

The very generalized instructions go like this (thanks caljohnsmith):

> If you change your fstab to to use the new swap partition UUID, you should be able to get swap working again, but the disadvantage of that approach is that you probably won't have a Ubuntu splash screen on start up any more. The reason is because the swap partition UUID is hard-coded in all your /boot/initrd images, so you would also have to regenerate all of the initrd images to use the new swap UUID. So instead of taking that approach, I would recommend simply changing your swap partition UUID to the UUID of your original swap partition, and then that should fix everything. To do that, first do:
 cat /etc/fstab | grep swap
 cat /etc/initramfs-tools/conf.d/resume
 If the swap UUID in both those files agrees, then copy/paste that UUID into the following command:
 sudo mkswap -U <original swap UUID> /dev/sdXY
 sudo swapon -a
 And of course replace "sdaXY" with the swap partition. Then you should have your swap back and also your Ubuntu splash screen the next time you reboot. You can check to make sure you have swap working with:
 free
 And that will show you both your RAM and swap usage.

---

### Post by superkid333 on 2017-04-11
Hi KansasNoob,

Thank you very much. I'm back on Ubuntu. I was able to make the partition using gparted from a live ubuntu USB. Originally, I had a gap between /boot and /home (which was my old swap). So I moved my /home back, and then created swap at the end - as predicted it is now /dev/sda7. 

So my sudo parted -l looks like this:
```

Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  525MB   524MB   primary   ntfs            boot
 2      525MB   6968MB  6442MB  primary   ntfs            diag
 3      6968MB  330GB   323GB   primary   ntfs
 4      569GB   1000GB  431GB   extended                  lba
 5      569GB   589GB   20.5GB  logical   ext4
 6      589GB   984GB   394GB   logical   ext4
 7      984GB   1000GB  16.4GB  logical   linux-swap(v1)



```

Checking the prior UUID using cat /etc/fstab | grep swap produced this output, which is expected as well (a good sign)
```

# swap was on /dev/sda5 during installation
UUID=9acc3489-4a18-4b9b-971d-116cd6c06f57 none            swap    sw              0       0

```

And cat /etc/initramfs-tools/conf.d/resume produced this output, also good:
```

RESUME=UUID=9acc3489-4a18-4b9b-971d-116cd6c06f57

```

Now for the fun part! Based on the instructions, my UUID code matches, so I should be able to do this fairly easily. 

And the beautiful outcome of "free":

```

              total        used        free      shared  buff/cache   available
Mem:        8062308      941768     6179764       20628      940776     6812108
Swap:      15997948           0    15997948

```

Thank you again for the help. Ubuntu (and Linux in general) is an amazing community. Thank you everyone for your help. Problem solved. Now others can google this thread and find help for years to come... Until 17.04 comes out and we can use swap files :)

---

### Post by SeijiSensei on 2017-04-11
> **superkid333 said:**
> I looked into a swap file, however from what I read on the Swap FAQ for Ubuntu, it doesn't currently support it
[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_a_swap_file.3F)
I only saw a warning that swap files were incompatible with btrfs file systems.  Ubuntu uses ext4 out-of-the-box.

---

### Post by Bucky Ball on 2017-04-11
> **superkid333 said:**
> Problem solved. Now others can google this thread and find help for years to come... Until 17.04 comes out and we can use swap files :)

If others know it is solved, that is. Please mark the thread 'Solved' using Thread Tools at top right of page or follow the last link in my signature for how. 

Not sure what you mean with the last bit. We can now, and always have been able to, use /swap partitions with Ubuntu. :-k

Anyhow, good luck and glad you got there in the end. :)

---

### Post by kansasnoob on 2017-04-11
> **superkid333 said:**
> Hi KansasNoob,

Thank you very much. I'm back on Ubuntu. I was able to make the partition using gparted from a live ubuntu USB. Originally, I had a gap between /boot and /home (which was my old swap). So I moved my /home back, and then created swap at the end - as predicted it is now /dev/sda7. 

So my sudo parted -l looks like this:
```

Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  525MB   524MB   primary   ntfs            boot
 2      525MB   6968MB  6442MB  primary   ntfs            diag
 3      6968MB  330GB   323GB   primary   ntfs
 4      569GB   1000GB  431GB   extended                  lba
 5      569GB   589GB   20.5GB  logical   ext4
 6      589GB   984GB   394GB   logical   ext4
 7      984GB   1000GB  16.4GB  logical   linux-swap(v1)



```

Checking the prior UUID using cat /etc/fstab | grep swap produced this output, which is expected as well (a good sign)
```

# swap was on /dev/sda5 during installation
UUID=9acc3489-4a18-4b9b-971d-116cd6c06f57 none            swap    sw              0       0

```

And cat /etc/initramfs-tools/conf.d/resume produced this output, also good:
```

RESUME=UUID=9acc3489-4a18-4b9b-971d-116cd6c06f57

```

Now for the fun part! Based on the instructions, my UUID code matches, so I should be able to do this fairly easily. 

And the beautiful outcome of "free":

```

              total        used        free      shared  buff/cache   available
Mem:        8062308      941768     6179764       20628      940776     6812108
Swap:      15997948           0    15997948

```

Thank you again for the help. Ubuntu (and Linux in general) is an amazing community. Thank you everyone for your help. Problem solved. Now others can google this thread and find help for years to come... Until 17.04 comes out and we can use swap files :)

Yes, community is everything! I learned that trick from *[COLOR="#0000FF"]caljohnsmith[/COLOR]* many moons ago. I fear he met an untimely demise because our last communication indicated that he was quite ill, but his great work lives on.

---

### Post by superkid333 on 2017-04-16
> **Bucky Ball said:**
> If others know it is solved, that is. Please mark the thread 'Solved' using Thread Tools at top right of page or follow the last link in my signature for how. 

Not sure what you mean with the last bit. We can now, and always have been able to, use /swap partitions with Ubuntu. :-k

Anyhow, good luck and glad you got there in the end. :)

Thanks! Marked it as "SOLVED". And about the last part, I was differentiating between swap files and swap partitions. I've always used a swap partition, but I only heard of swap files recently. In reading the swap file page, I thought that Ubuntu isn't using swap files yet - only partitions - however, perhaps I was wrong and swap files can be used.

---

### Post by SeijiSensei on 2017-04-17
Look at the [manual page for mkswap]("https://linux.die.net/man/8/mkswap").  It shows you how to create a swap file using dd and mkswap, and how to activate it with the swapon command.  I've used this method a number of times over the years, and just tested it again successfully on a 4.4.0-64 kernel.

---

