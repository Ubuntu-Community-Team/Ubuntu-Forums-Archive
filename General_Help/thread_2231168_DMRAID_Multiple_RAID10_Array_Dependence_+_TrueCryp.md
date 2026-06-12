---
title: "DMRAID Multiple RAID10 Array Dependence + TrueCrypt Can't Access Secondary Array"
date: 2014-06-23
forum: General Help
---

### Post by The00Dustin on 2014-06-23
I'm not new to linux, but I was trained in the ways of RedHat (actually CentOS/Fedora, but close enough), so Ubuntu/debian is still a bit foreign to me.  I'm also a bit out of practice, as I mostly only use Linux to manage Windows disks (via PartEd Magic mostly, but using ntfsutils and DD, not the GUI).

 In order to get as far as I am, I had to learn how FakeRAID isn't ideal in linux, but I am running Windows on the same drives, and don't want to virtualize it, so I stuck with FakeRAID in spite of its problems.  I would actually use real RAID, but my real RAID controller is SATA II and I am using some SATA III SSDs in this configuration.  That having been said, I had a heck of a time installing Ubuntu 14.04 on a LUKS partition on a FakeRAID volume.  I finally got that done, and now I'm having trouble using TrueCrypt to open Windows partitions on another FakeRAID volume, which appears to potentially be related to the same DMRAID behavior.

 First and foremost, let me explain my actual RAID configuration, because this could be something DMRAID simply doesn't fully support.  I have four SSDs set up in a RAID10 (which is, unfortunately, RAID0+1 on this particular chipset).  More specifically, I have them set up in **TWO** RAID10 arrays, which I will refer to as RAID10SSDP1 and RAID10SSDP2.  My original problem was that DMRAID doesn't mount the second array automatically, so installing Ubuntu there seemed unlikely to work even if everything else went perfect (it didn't, the machine doesn't support UEFI [8-core FX processor, but no UEFI BIOS, seems odd to me], and the ACPI implementation is bugged, so it took quite a while to even learn to get the Ubuntu CD to boot on this machine).

 In hindsight, given that I'm not getting RAID1+0 out of this, the perfect answer to my problem is probably to redo everything and end with two RAID1 arrays (one FakeRAID, one MD RAID or LVM) instead of a RAID0+1 array that doesn't really add any additional fault tolerance.  However, I don't really want to do that since I have both operating systems installed and configured to some degree and I don't have a lot of free time to mess with all of this (backing up Windows again and restoring it to RAID1 plus re-installing Ubuntu using something other than DMRAID and losing what I've already set-up therein).  Moreover, I wouldn't mind helping to get a bug fixed in DMRAID if one exists.

 I already backed up the boot sector and partitions from RAID10SSDP1 using Ubuntu Desktop 14.04 in LiveCD mode so that I could delete and re-create the RAID10 arrays after secure-erasing the SSDs to make sure I don't lose any performance, and I re-created RAID10SSDP1 at the size RAID10SSDP2 was (and vice versa).  I also already restored the backed up RAID10SSDP1 data to RAID10SSDP2.  Windows boots fine and doesn't even know anything is different.  Ubuntu is installed on RAID10SSDP1 since that solves the DMRAID auto-detect problem.  If I didn't have to disable ACPI and make a minor mistake in grub.conf because of that, installing Ubuntu on LUKS would have been the easy part.

 All of that having been said, I'm going to delve into the details of the DMRAID issue, but first, I want to define what I am referring to:
 1)  /dev/mapper/pdc_dd is the beginning of the name of the DMRAID auto-activated array, but since I don't know the whole name, I am going to substitute pdc_dd... with pdc_RAID10SSDP1
 2)  /dev/mapper/pdc_de is the beginning of the name of the other DMRAID array, which isn't activated during boot due to detected conflicts or something.  Again, since I don't know the whole name, I am going to substitute pdc_de... with pdc_RAID10SSDP2

 So, when Ubuntu 14.04 boots (LiveCD or installed copy), DMRAID messages pop up regarding the disabling of partition tables on a few dm-#'s since they are components of another dm-# (which is pdc_RAID10SSDP1).  Additional DMRAID messages pop up regarding not activating at least one more dm-# (and maybe additional dm-#s) due to a conflict or something.  I'm not in Linux and want to get this posted while I have time, so I don't have access to logs at the moment, but I will be glad to post more specific information from logs later if someone can confirm that this behavior isn't expected based on my configuration).  Once I'm in Ubuntu, dmraid -s will show the active superset (pdc_RAID10SSDP1) and the inactive superset (pdc_RAID10SSDP2).  dmraid -ay will activate pdc_RAID10SSDP2 with output something like this:
 pdc_RAID10SSDP1 already activated
 pdc_RAID10SSDP2-0 successfully activated
 pdc_RAID10SSDP2-1 successfully activated
 pdc_RAID10SSDP2 successfully activated

 Prior to activation, /dev/mapper has the following:
 pdc_RAID10SSDP1-0 - this is RAID0 component
 pdc_RAID10SSDP1-1 - this is RAID0 component
 pdc_RAID10SSDP1 - this is RAID0+1
 pdc_RAID10SSDP11 - this is /boot
 pdc_RAID10SSDP12 - this is encrypted LUKS container (root)

 After activation, the following are added:
 pdc_RAID10SSDP2-0 - this is RAID0 component
 pdc_RAID10SSDP2-1 - this is RAID0 component
 pdc_RAID10SSDP2 - this is RAID0+1
 pdc_RAID10SSDP21 - this is Windows boot TC container
 pdc_RAID10SSDP22 - this is C:\ TC container

 I'm pretty sure all of this is accurate, and I'm guessing it all sounds normal enough other than the part about the messages about not activating some dm-# devs during boot.  That having been said, I am now going to describe some behavior I saw in the Ubuntu 14.04 Live CD before installing.  Specifically, I ran dmraid -an to deactivate pdc_RAID10SSDP1 and then ran dmraid -ay pdc_RAID10SSDP2 in order to activate pdc_RAID10SSDP2.  DMRAID behaved as if pdc_RAID10SSDP2 was dependent on pdc_RAID10SSDP1 and re-activated it as well.  This is one bit of behavior I'm not sure is normal (and I am open to the possibility that it is normal, or even a bug in my BIOS and not in DMRAID).

 So, that's the DMRAID issue, and now I am going to post about the TrueCrypt issue (in the same thread because the configuration information above is relevant).  That issue is simpler to explain.  Basically, when I try to mount /dev/mapper/pdc_RAID10SSDP22 using TrueCrypt, I get an error that states something like /sys/block/pdc_RAID10SSDP2/pdc_RAID10SSDP22/start doesn't exist, and when I look in /sys/block, I don't see pdc_anything, only the dm-#'s.  I can see I the disk application (because only the RAID0+1 dm-#s show partitions there) and in something else (I don't remember what) which dm-# I need to use in order to connect to pdc_RAID10SSDP2, but the dm-#'s don't show up with partitions so I can't mount a specific partition using /dev/dm-# from TrueCrypt.  Based on this thread (couldn't find anything similar in this forum): [http://www.linuxquestions.org/questi...ubuntu-775564/]("http://www.linuxquestions.org/questions/linux-newbie-8/mounting-a-raid-0-with-truecrypt-on-it-ubuntu-775564/") I'm pretty sure (but not positive since the steps to resolution aren't actually posted) that I should be able to mount using the /dev/mapper path that I tried.

 Sorry for the super long post.  Any input on either issue?  TIA

---

### Post by The00Dustin on 2014-06-23
OK, you probably have to read the post above for this to make sense, but in order to make sure it is clear, the two things that I would like to find out whether or not are normal follow:
 1) DMRAID doesn't auto-activate second array on same set of disks
 2) DMRAID can't activate second array on same set of disks without activating first array

Also, in case anyone notices this thread is a duplicate of a thread on another forum, that was due to problems signing up with Ubuntu One yesterday, but I will keep both threads updated with any relevant follow-up information.

---

