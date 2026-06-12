---
title: "Looking for set-up instructions for chain loading to dual boot Ubuntu/Kubuntu"
date: 2014-04-27
forum: General Help
---

### Post by wanderingarticfox on 2014-04-27
I am just looking to see where I might find instructions on how to use the Alt. ISO to set up chain-loading via a boot partition. I want to instal Ubuntu and Kubuntu as a dual boot on a sigle hard drive. I know I will need a logical partition for swap but I am not clear on how to set up the /boot partition using the Alt. Instal CD/DVD ISO. Thx in advance for the help :D    I 've been looking around and it seems I might need to use the 'server' iso to create the MBR in the /Boot,. I also have not found a listing for the 14.04 Alternate ISO listed but it may be I get the choice at the time of the download? or is that no longer an option?    [http://www.hentzenwerke.com/wp/installingmultiplelinuxdistributions_onasinglebox.pdf](http://www.hentzenwerke.com/wp/installingmultiplelinuxdistributions_onasinglebox.pdf)    this is the place I found some information but could still use some help.

---

### Post by Bashing-om on 2014-04-27
wanderingarticfox; Hi !

Not a big deal at all, just Prior Prudent Planning .
Keep in mind what is to be your primary operating system, that is the system that should control the booting process.
In the present operating system - prior to installing the dual booting operating system - disable grub's 30_os-prober . -> update grub for the change to take effect.
Now if you are not comfortable with intensive partitioning on your own, let the install wizard take care of all the details -> Choose the install option "install along side" .

The last installed system becomes the primary booting system until you dictate other wise. If you are happy with that system as the primary, all done - leave well enough alone.
Else -> in the install that you want as the secondary, turn off grub's 30_prober , update grub and in what you want for that primary; turn 30_os-prober back on and update grub once more to pick up that secondary install and chainload it to the primary's grub.

Remember, only 1 OS can control booting, one MUST keep it clean behind them as to what is dictated in that boot process. 
Turn off -> update for the change to take effect
Turn on -> update for the change to take effect.

Need guidance to turn off/turn on ?
These are the majority ( there are others) of the files that control what the main boot control file will contain:
```

ls -la /etc/grub.d

```
the file '30_os-prober' is the one of interest here, to turn it off:
```

sudo chmod -x /etc/grub.d/30_os-prober

```
to turn 30_os-prober back on
```

sudo chmod +x /etc/grub.d/30_os-prober

```
And to update grub's boot control file '/boot/grub/grub.cfg' , do:
```

sudo update-grub

```
For the better place to start learning grub:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Have yet to see better than drs305's tutorial .

[INDENT][INDENT][INDENT]piece of cake
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-27
Do not share a /boot partition, you will get conflicts. And generally just better not to have a /boot partition with either install.
You can share swap if you do not hibernate nor encrypt either install.

Often better to partition in advance and use Something else to manually select partition for / (root). If swap exists it finds it. But if regularly booting into both installs you may want a shared data partition also. Then you can more easily access the same data from both installs.

If your installs are all Debian based, you can manually add simplified boot stanzas to directly boot the most current kernels in your other install without having to run sudo update-grub in both installs.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by coffeecat on 2014-04-27
Not a Tutorial

*Thread moved to **General Help**.*

---

### Post by wanderingarticfox on 2014-04-28
"Often better to partition in advance and use Something else to manually select partition for / (root). If swap exists it finds it. But if regularly booting into both installs you may want a shared data partition also. Then you can more easily access the same data from both installs."

I plan to use Ubuntu for my 'everyday' computing needs and Kubuntu for Free CAD.

If I plan to partition as follows:

/dev/sda 1    swap     16000mb              [I have 16gigs of RAM]
/dev/sda 2       ?        500,000mb           [Ubuntu 14.04 64bit main OS]
/dev/sda 3       ?        750,000mb           [Kubuntu 14.04 64bit]
/dev/sda 5       ?        remander of 1.5 TB HHD

I'm off to look at and study the links provided  before I even download and burn DVD's for installation, just rusty on what type of partition to use {reason for ? above}. 
Thought I'd put that out there for now.  Thx for the links everyone.

---

### Post by Bashing-om on 2014-04-28
wanderingarticfox; Hello.

Considerations: 
Is this hard disk formatted as GPT ? - Larger disk often are and that is a good thing. 
Then one must provide a small separate boot partition.

If this hard disk is partitioned as the legacy msdos;
Then I would highly recommend an extended partition be made ( msdos format has a limit of 4 primary partitions) [one of those primary partitions being 'extended' to contain logical partitions -> one of these 'logical partitions' be made as the swap partition].

Other wise, the size of the partitions will work well, one can fine tune at a later time, when more experience with your system dictates better.

[INDENT][INDENT]there is no substitute
[INDENT][INDENT][INDENT]for experience
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-28
If you have 16GB of RAM you will never use swap unless you hibernate and if dual booting hibernation is not recommended. (and you would need two swaps if hibernating).
I would just have maybe 2GB for swap just to have some.

I now prefer gpt partitioning, but not required. I add an efi partition to the beginning of all gpt drives so if I move drive to a new system I can convert to UEFI boot easily.

I also prefer smaller / (root) partitions of 20 to 25GB and separate data partition(s) if dual booting Linux installs.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by wanderingarticfox on 2014-04-28
> **Bashing-om said:**
> 

If this hard disk is partitioned as the legacy msdos;
Then I would highly recommend an extended partition be made ( msdos format has a limit of 4 primary partitions)

This HDD has never had Dos; thanks for the note though; I fired Microsoft years ago; I do not like the marketing Dept. there; the rest of the folks are just fine.
It is a WD so I am sure the HDD was formatted for DOS but I only need the following break down.

Thinking about :

/dev/sda 1 /swap  16,000mb
/dev/sda 2 /home  500,000mb
/dev/sda 3 /home  750,000mb
/dev/sda 4 /data    remaining of 1.5 TB HDD

I know this seems restricted but I will not want to access the Free CAD of sda 3 from the everyday use of sda 2  {Kubuntu ; Ubuntu respectively}
Thx for links OldFred

---

### Post by wanderingarticfox on 2014-05-02
Ref. "Beginning the LINUX Command Line"  by Sander van Vugt >>>> This book has providded more information than this Forum; This Forum seems to be centered on joining DOS to Linux.
  I have no intrest in DOS; My intrest is in LINUX OS and compatability. If Ubuntu is truely a Linux 'free source' then it  should be primarily a Linux focused  software system. Shame on you to promote microsoft links. I will look to Kubuntu for help!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by oldfred on 2014-05-02
MBR or msdos partitioning is not DOS, just the same partitioning as used with PCs since the first PC.
The only real alternative is now gpt partitioning which is used with all new UEFI systems. Apple converted to UEFI with gpt when it changed to Intel chips. Microsoft uses UEFI with gpt for all new Windows 8 pre-installed systems.

 MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

