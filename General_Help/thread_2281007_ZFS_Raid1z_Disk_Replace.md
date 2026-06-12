---
title: "ZFS Raid1z Disk Replace"
date: 2015-06-03
forum: General Help
---

### Post by egrimisu on 2015-06-03
[COLOR=#111111][FONT=Ubuntu]I have been running ZFS Raid1z with 5 disk under Ubuntu 12.04 for 3 years now with no problems at all.

Unfortunately the day of failing disk has come. I have lost a disk in the array, he simply went offline and after a few days the second one started to drop errors as well. As the system detected check sum errors on the second disk that has started to fail (some bad sectors according to SMART) it started to re-silver the array and when i got to the PC and saw the re-silvering was already at 40%, in order to avoid a catastrophe I have decided to stop the server asap.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So basically my array looks like almost like this, and somewhere it is mentioned that data's were lost :[/FONT][/COLOR]
   NAME                                    STATE     READ WRITE CKSUM
    Misu                                    DEGRADED     0     0     0
      raidz1-0                              ONLINE       0     0     0
        scsi-SATA_ST3000DM001-9YN_Z1F1587B  OFFLINE      0     0     0   (failed hdd)
        scsi-SATA_ST3000DM001-9YN_Z1F14J7V  ONLINE       0     0     0
        scsi-SATA_ST3000DM001-9YN_Z1F14JYL  ONLINE       0     0     0
        scsi-SATA_ST3000DM001-1CH_W1F1G04F  ONLINE       0     0     0
        scsi-SATA_ST3000DM001-1CH_W1F1G1H7  ONLINE       134   5     139 (failing hdd)


[COLOR=#111111][FONT=Ubuntu]Since the resilver process take some time i'm quite afraid of replacing the first disk and hope that the second one, the one that has checksum errors will not fail. So i have decided to replace the PCB on the first failed disk since it had pcb problems and not mecanical problems.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So, if i manage to make the first disk running what shall i do next, how will zfs know that the disk was not replace (not sure but i believe that changing the pcb will change the serial number and stuff for that disk) and detect the disk as the original member?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any other information that can help me not to make this worse?[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-06-04
As you know, RAID is not a backup solution and many RAIDs fail during the recovery/resilvering process because the thing that caused one drive to fail is also a factor in the other drives (old age in this case).  Replacing a PCB in a drive is not trivial.  There are digital calibrations stored on the PCB that may not transfer to the bad hard drive.  So, don't get your hopes up about simply changing a PCB and hoping to revive a disk drive.

I would allow the resilver process to continue.  If it is successful, then you only lose a few files that were stored on the bad sectors and ZFS will point out which files have suffered bit-rot.  

Check your power supply, make sure you have decent power, because a sagging power supply can cause this type of failure.  If the resilver fails because of a second catastropic disk failure, then you are still in the same situation, a failed ZFS pool and limited ability to recover.

---

### Post by egrimisu on 2015-06-04
I was allways aware that this could happen on any raid system, but budget was limited to create a raid6 or create a good archiving solution. A new powersupply is allready on it's way since i konw that sometimes disks fail because of it.

I might be able to clone the failed disk on another one, I got another disk with the same pcb (same serial, same model, same firmware) and i intend to swap them and keep the rom. Still, that will chane the serial number of the disk, so after that the bigest question is how to let know zfs that i have change only the serial number of the disk and not the whole disk so a resilver of that disk is not required.

---

### Post by tgalati4 on 2015-06-04
That's true, I don't know of a way to recode the disk.  I'm not sure if ZFS uses UUID to keep track of disks in the pool or if it simply uses the headers that are written to it to keep track of the disk order.  You will find out soon enough.  Let us know how the PCB swap works out.

---

### Post by egrimisu on 2015-06-19
> **tgalati4 said:**
> That's true, I don't know of a way to recode the disk.  I'm not sure if ZFS uses UUID to keep track of disks in the pool or if it simply uses the headers that are written to it to keep track of the disk order.  You will find out soon enough.  Let us know how the PCB swap works out.

Hi again,

So the PCB swap did not work unless i have swapped the ROM also, after the ROM swap the drive started finely but had the same issues it seems that in fact the disk was broken and not the PCB.

Now this leaves me with raid1z with 1 drive failed completely and with one on the verge to fail aswell.


What do do?
1. Shall i power up the server and wait for the resilver to finish with only 4 drives in the array and after it completes if it complete add the fifth new one?
2. Add the fifth disk, wait for resilver to complete
3. Backup as much data as I can on external drives and after add the new drive ( resilver might autostart, shall i cancel it or not)?
4. Backup important data  and after add the new drive ( resilver might autostart, shall i cancel it or not)?

So the question is, what to do next to be as safe as possible?

---

