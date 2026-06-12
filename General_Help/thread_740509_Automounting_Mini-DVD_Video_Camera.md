---
title: "Automounting Mini-DVD Video Camera"
date: 2008-03-30
forum: General Help
---

### Post by Sleestack on 2008-03-30
I want to temporarily mount my video camera which uses a mini-DVD disk as storage so I can transfer files to my computer. However, after plugging it into the USB port and turning it on, the camera does not automount. The video camera is the only device I'm having a problem with, digital still cameras, USB flash drives, and other external storage all automount correctly. 

I've done some searching and the following commands seemed to pop-up frequently in the forums, and although I'm not exactly familiar with what they do I figure it's worth posting the results for "lsusb", "dmesg", "mount" and "fdisk".

Comparing "lsusb" before and after plugging-in the camera, I see this identifies the video camera (it's a Sony DCR DVD-405):

[FONT="Courier New"]Bus 001 Device 017: ID 054c:00c1 Sony Corp.[/FONT]

"dmesg" returns this result: 

[FONT="Courier New"][108988.912000] sr 11:0:0:0: [sr1] Sense Key : Blank Check [current] 
[108988.912000] sr 11:0:0:0: [sr1] Add. Sense: No additional sense information
[108988.912000] end_request: I/O error, dev sr1, sector 0
[108989.032000] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[108989.032000] sr 11:0:0:0: [sr1] Sense Key : Blank Check [current] 
[108989.032000] sr 11:0:0:0: [sr1] Add. Sense: No additional sense information
[108989.032000] end_request: I/O error, dev sr1, sector 0
[108989.176000] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[108989.176000] sr 11:0:0:0: [sr1] Sense Key : Blank Check [current] 
[108989.176000] sr 11:0:0:0: [sr1] Add. Sense: No additional sense information
[108989.176000] end_request: I/O error, dev sr1, sector 0
[108989.328000] sr 11:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[108989.328000] sr 11:0:0:0: [sr1] Sense Key : Blank Check [current] 
[108989.328000] sr 11:0:0:0: [sr1] Add. Sense: No additional sense information
[108989.328000] end_request: I/O error, dev sr1, sector 0
[/FONT]

"fdisk" returns this: 

sudo fdisk -l
[FONT="Courier New"]
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834       23845   128616211    7  HPFS/NTFS
/dev/sda3           23846       38295   116069625   83  Linux
/dev/sda4           38296       38913     4964085    5  Extended
/dev/sda5           38296       38913     4964053+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x595ec772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdh: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7ff6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1        7295    58597056    7  HPFS/NTFS

Disk /dev/sdg: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6adf6ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1        4863    39062016    7  HPFS/NTFS[/FONT]

And finally, "mount":

[FONT="Courier New"]/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdh1 on /media/Apollo60 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/MaxtorExternal type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdg1 on /media/Artemis40 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)[/FONT]

From what I can see, "lsusb" gives me at least some hope the computer is recognizing *something* gets attached to the machine, but overall I see nothing I can use to mount the device. Suggestions or examples are greatly appreciated.

---

