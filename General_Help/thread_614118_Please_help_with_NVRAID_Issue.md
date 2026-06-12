---
title: "Please help with NVRAID Issue"
date: 2007-11-15
forum: General Help
---

### Post by Em-Buntu on 2007-11-15
Hello All

I have a need for support in getting my RAID-0 recognized under Gutsy Gibbons.

Here's the background;

I have a workstation that is configured to boot either Windows XP-64 or Ubuntu-64 Gusty Gibbons.

Win XP 64 is installed on a 200GB drive (C:)

Ubuntu is installed on a 89GB drive (D:)

I have a 1TB RAID-0 (3x400GB SATA)  installed using the NForce-4 chipset (no boot) for backup and to hold my music development files.

Problem:
I have the RAID installed where I can access it under Win XP. The RAID is NTFS. 

I have never setup the RAID under Ubuntu for fear of possibly losing the data on the RAID. However, I am now hearing that Ubuntu can be setup to r/w RAID using NTFS. Is this correct?
So, the question I have is,
How do I setup RAID support under Ubuntu without using any partition or formating? All I want to do is mount and access for reads/writes. 
Is this possible?

Thanks in advance for any assistance.  :popcorn:

---

### Post by njparton on 2007-11-15
For best compatibility (and performance) you need to go for hardware raid such as 3ware or a high end highpoint card.

3ware drivers are built into the kernel.

For software raid (that you're using) you are relying on the manufacturer releasing a compiled driver or source code for you to compile.  Check out the nvidia website, I'm not sure if what you need exists.

If you haven't got the cash to splash on a 3ware card, buy a cheap highpoint software raid card, they have drivers for the latest kernel available.

---

### Post by Em-Buntu on 2007-11-15
Thanks for the response, but that is not a feasible or desired option.

---

### Post by njparton on 2007-11-15
You can't use software raid if the drivers don't exist. Check that first.

Otherwise if you really want raid then you're going to have to buy something I'm afraid.

---

### Post by Em-Buntu on 2007-11-15
That would mean I'd lose all of the data currently on the drives.
I'm trying to avoid any loss of data.
Since these RAID devices are on the majority of motherboards, drivers must exist.
I'll have to check with NVIDIA to see if they offer linux equivalent drivers.

Update:
After checking the Nvidia forum, at appears that Nvidia cares little for supporting Linux with RAID Manger or Media Shield.
Perhaps you are right and I should look at upgrading to a REAL RAID card to save myself future grief.
LOL, that sux cause then I'll have three RAID controllers (Silicon Image, NVIDIA, 3 COM) in the box of which only 1 is used.

---

### Post by gimmic on 2007-11-15
I've got exactly the same problem right now. 1TB(2x500) raid0 is useless for me. I think the raid will function properly if we reformat it as ext3, but what to do with the 850~GB of data meanwhile?

Related thread here: [http://ubuntuforums.org/showthread.php?t=614047](http://ubuntuforums.org/showthread.php?t=614047)

---

### Post by Em-Buntu on 2007-11-15
Well I just cautiously experimented with installing DMRAID.
Using DMRAID-r, it see the three disks, and sees they are organized a a striped raid. However, that's all the information it provides. Is there a MOUNT command in DMRAID, or is this elsewhere.

I also have the NTFS Configuration tool installed, but it doesn't seem to see the RAID when started. If I suceed in mounting the RAID will NTFS Configurator see it and allow reads/writes?

The only reason I'm attempting to use Ubuntu is Win XP-64 is sort of flaky and seems to have a problem with NVRAID using SATA also.

I think NJPARTON may be right about these cheap sw RAID implementations. They may be more trouble then they are worth.

---

### Post by Em-Buntu on 2007-11-15
> **gimmic said:**
> I've got exactly the same problem right now. 1TB(2x500) raid0 is useless for me. I think the raid will function properly if we reformat it as ext3, but what to do with the 850~GB of data meanwhile?

Related thread here: [http://ubuntuforums.org/showthread.php?t=614047](http://ubuntuforums.org/showthread.php?t=614047)

Yes, that is the issue.
I simply want to read/write the raid in ntfs, not reformat it to ext3. Then I'd have no access in Windows XP.
This is not a good situation.
It seems the only good solution is a hardware RAID controller supported by both OSs.

---

### Post by gimmic on 2007-11-15
> **Em-Buntu said:**
> Yes, that is the issue.
I simply want to read/write the raid in ntfs, not reformat it to ext3. Then I'd have no access in Windows XP.
This is not a good situation.
It seems the only good solution is a hardware RAID controller supported by both OSs.

Ah I didnt think about that(trying to go full time). If you have not tried already, look at ntfs-3g. Try that and let me know what you got before you try kpartx or anything.

At first I was getting I/O errors, now the mount just fails.

---

### Post by Em-Buntu on 2007-11-16
Thanks for the response.

I've tried ntfs-3g but it's no use if the system cannot see/build/recognize the RAID.
At this point, Gutsy only sees one of the disks, and I can't afford to allow it to access it for fear of losing data.

Otherwise, I love Ubuntu, but it's a pain to switch the system to windows everytime I need to access the RAID. If I could read/write the RAID, I'd use Windows that much less.

---

### Post by Velociraptor on 2007-11-20
(Sorry, I'm not at my ubuntu machine, so this is from memory...)

I think dmraid is the way to go. As you said "dmraid -r" should list the detected raid devices (without making any changes).

You then need to do a "dmraid -a y" to active those devices. That is, your raid drive and partitions should be listed as devices in /dev/mapper.

You can then mount them to any directory of your choosing, e.g., 

sudo mkdir /myraid
sudo mount /dev/mapper/nvidia_bggfdgec2 /myraid

I think mount should recognise that its an ntfs formatted partition. If you get that working, it may be easier to add entries to the /etc/fstab file, so that your raid partition is automatically mounted on boot.

---

