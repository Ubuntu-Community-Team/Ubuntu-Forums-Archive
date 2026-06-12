---
title: "cannot find GRLDR in all devices Press CTRL ALT DELETE"
date: 2013-01-28
forum: General Help
---

### Post by ArlieS on 2013-01-28
I've been running Ubuntu 12.04.01 LTS, installed on top of windows 7 with WUBI, for almost 2 months.  This morning Ubuntu declined to boot. The complain was something like:

Try (hd 0,0): NTFS5: no wubildr
      Try (hd 0,1): NTFS5: 2
      Try (hd 0,2): invalid or null
      Try (hd 0,3): invalid or null
Error: Cannot find GRLDR in all devices.
      Press ctrl+Alt+Del to Restart

The solution suggested at [http://ubuntuforums.org/showthread.php?t=1719333](http://ubuntuforums.org/showthread.php?t=1719333) did not work for me. (Note - I only copied 2 files, as suggested in the post, not the 3 files suggested in the first reply, since I'm unclear what the 3rd file was supposed to be.)

I'd be very interested in knowing whether there's any difference in the relevant files between 12.04.01 and 12.10.  The only substantially odd thing about my installation is that I'm using apt pinning to let me use a small number of packages from 12.10 - none of which involve system start up, but perhaps I somehow installed the wrong version of something I didn't intend to.

The other possibility is a corrupt file system. I don't believe I've had a recent crash, but the 2nd time I booted to windows after the first Ubuntu boot failure, it insisted on running CHKDSK and made a number of corrections. Where it named the files affected, they were files on the native NTFS partition which had been placed there by Ubuntu, which suggests other interesting unpleasant possibilities.

---

### Post by Mark Phelps on 2013-01-28
> **ArlieS said:**
> ...The other possibility is a corrupt file system. I don't believe I've had a recent crash, but the 2nd time I booted to windows after the first Ubuntu boot failure, it insisted on running CHKDSK and made a number of corrections. Where it named the files affected, they were files on the native NTFS partition which had been placed there by Ubuntu, which suggests other interesting unpleasant possibilities.
If you're writing into the Windows filesystem while running Ubuntu, that is generally a BAD idea.  Real easy way to corrupt the Windows filesystem.

---

### Post by ArlieS on 2013-01-28
> **Mark Phelps said:**
> If you're writing into the Windows filesystem while running Ubuntu, that is generally a BAD idea.  Real easy way to corrupt the Windows filesystem.


Ouch! I thought linux' NTFS support was no longer that fragile, and the wubi installation refused to claim as much of my disk for ubuntu as I wanted it to - I've got some very large source trees unpacked onto the NTFS side so as not to overflow the linux file system.  At least I haven't been compiling in there ;-)

---

### Post by oldfred on 2013-01-28
It is not that the Linux NTFS driver is not pretty good now, but that Windows does not like too much activity in its system partition from external sources.

If you really want dual boot and a large Linux partition then you have to do a full partitioned install. Wubi is restricted to 30GB and is running on the NTFS file system so is not quite as reliable.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by ArlieS on 2013-01-28
> **oldfred said:**
> If you really want dual boot and a large Linux partition then you have to do a full partitioned install. Wubi is restricted to 30GB and is running on the NTFS file system so is not quite as reliable.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

Thank you very much for the links. I guess I'll be going full dual boot. Hopefully I can do the migration from a rescue DVD. 

My original goal wasn't to try Ubuntu - I'm a happy single-boot Ubuntu user at home - but to preserve the windows environment IT had given me on my office machine, without having to actually use windows except perhaps when demonstrating a hardware problem to IT. One of my coworkers had taken this path before me without encountering any problems, but it turns out he spends 90% of his time booted on windows.  Hopefully I can move to a true dual boot without breaking ITs windows environment environment.

---

### Post by oldfred on 2013-01-28
Most companies lock system even USB ports.

But if you can boot a USB port, you can put a full install on a flash drive or external hard drive. Flash is not speedy but functional if you have a fair amount of RAM and change a few settings to reduce writes. A lightweight version also loads a bit faster. I have full Ubuntu on my 16GB flash drive more as a back-up or test install, so I do not use it heavily. 

       HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

    
       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
       Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

            Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

