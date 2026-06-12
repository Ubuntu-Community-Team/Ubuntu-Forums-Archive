---
title: "Identifying failed drive Raid5"
date: 2014-04-03
forum: General Help
---

### Post by XBNCPRk on 2014-04-03
After walking a friend through setting up a 20tb Raid5 array on a new media server, its been noticed that the drives dont maintain a constant /dev/sdX label. This isnt a problem since the boot drive is identified in fstab by UUID, and each of the array drives are flagged as raid members and assemble correctly in mdadm. 

My question is this, I understand that the /dev/sdX labels are assigned now on a first come first served basis on boot. So, when mdadm flags a drive, say /dev/sdd as failed, how will you know which physical drive it is, since you cant depend on sdd being plugged into the fourth port on your mobo?

(Im looking for something more concrete here than 'fail it out, and see which drive feels like its stopped writing')

---

### Post by tgalati4 on 2014-04-04
You have identified an interesting use case and possible bug when using mdadm and failure messages.

I don't know if you can change the drive's spin-up speed via *hdparm*, but that is one method.  Set each drive to a different spin-up delay and that would help with a consistent drive assignment.

A work-around would be to write a script to query your drives and save the log file at each boot:

tgalati4@Mint14-Extensa ~ $ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD1600BEVS-22RST0, FwRev=04.01G04, SerialNo=WD-WXC907006646
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

This way if any drive fails you can go to the log file and see the drive assignments for that boot.  The drive assignments may be captured in /var/log/syslog, you will have to scroll through the boot process to see how the drives are initially enumerated.

---

### Post by frostschutz on 2014-04-04
> **XBNCPRk said:**
> So, when mdadm flags a drive, say /dev/sdd as failed, how will you know which physical drive it is

You query it. The machine keeps running after all, as long as there is only one failed drive. So you can check your logs what happened exactly etc. and go from there. Identifying the drive has never been an issue for me in practice, even ignoring everything else...

If you prefer more in the ways of documentation, write down the device role and serial of each. Then the mdadm failure email will contain all the information you need.

For example:

```

This is an automatically generated mail message from mdadm
running on Ubuntu

A Fail event had been detected on md device /dev/md0.

It could be related to component device /dev/sdb1.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4]

md0 : active raid1 sda1[3]
      62519296 blocks super 1.2 [2/1] [U_]

unused devices: <none>

```

So there. It says [U_]. And that's the device roles like [0123456789]. So [U_] means the device with role 1 failed; [_U] role 0 failed, [UUUU_U] role 4 failed etc.

Compare with mdadm --detail output:

```
    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8       34        1      active sync   /dev/sdc2
       2       8       50        2      active sync   /dev/sdd2
       3       8       82        3      active sync   /dev/sdf2
       6       8       98        4      active sync   /dev/sdg2
       5       8      114        5      active sync   /dev/sdh2
       4       8       66        6      active sync   /dev/sde2
```

Ignore "Number", that's random. Important is the RaidDevice, that's the device role and it never changes, well, never until you remove drives and add them in a different order anyhow.

So with this information you can put into your documentation that /dev/sdf2 with serial 6234982349264 is the role 3 in your mdraid. So when mdadm sends you a failevent with [UUU_UUU] you'll know this to be the afflicted drive.

Ideally you created your RAID in port order in the first place, so even without documentation you'll know when you see [UUU_] that it's the drive in port 4 that failed and no other.

---

### Post by XBNCPRk on 2014-04-08
The problem isnt in determining which device fails. That, as you pointed out, is easily decribed in the failure notice itself. The problem is that the devices are assigned a label randomly with each start. For instance, my machine has an ssd for boot, and an 8-drive raid array. However on one start it may declare the ssd to be /dev/sde and the array to be made up of /dev/sd[abcdfghi] and on the next the ssd is /dev/sda and the array /dev/sd[bcdefghi]. 

Leaving aside that unfortunately seagate stopped edge labeling their hdds with the serial numbers, so to match it would require pulling them one at a time to check, what you may have in your documentation would only be relevant until the next reboot when theyre randomly assigned again.

---

### Post by frostschutz on 2014-04-08
> **XBNCPRk said:**
> The problem is that the devices are assigned a label randomly with each start.

Doesn't matter. That's what I tried to explain...

The mdadm failedevent message gives you both the device name - which  is useful enough while the box is still running, you login to it and  grab that device's serial or the others - as well as the role number  ([_UU] = 0, [U_U] = 1, [UU_] = 2 etc.).

If your case has bays that puts HDDs in a recognizable order, it's just  a matter of ordering the drives according to their roles in the raid.

> **XBNCPRk said:**
> seagate stopped edge labeling their hdds with the serial numbers, so to match it would require pulling them one at a time to check

I don't recall ever having an edge labelled HDD. If you need such labels, you can always do them yourself. Nothing a sticker or a tippex pen won't solve.

---

### Post by XBNCPRk on 2014-04-11
Im sorry, I dont mean to disparage your help, but Im afraid my point isnt coming across clearly. The drives do not maintain the same order or label between boots. Thus /dev/sde may be the drive in port 4 on the mobo for one boot, and the next time may be the drive in port 7. So what Im saying is yes, its very simple to determine that /dev/sdx failed, but nothing that says /dev/sdx is the one plugged into port y. The closest Ive been able to come is the disk utility and using it to match /dev/sdx to a port number. (Only problem with that is that some show up as sata controller attached drives, some show as pata attached, and somehow miraculously thinks theres a port 12 on a system with 6 mobo plugs, and a 4 plug pci-e card installed)

---

### Post by frostschutz on 2014-04-12
> **XBNCPRk said:**
> The drives do not maintain the same order or label between boots.

Right. But their role in the RAID does not change. That's the point I was trying to make, not sure if that got across to you.

You have a drive. It does not matter which /dev/sdx name it currently has. Let's assume it is /dev/sdx this time around.

You get the drive's serial number with hdparm or smartctl.

```

# hdparm -i /dev/sdx

/dev/sdb:

 Model=WDC WD20EARS-00MVWB0, FwRev=51.0AB51, SerialNo=WD-WMAZA0602133

# smartctl -A /dev/sdx
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.14.0] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0602133

```

You get the role with mdadm --examine.

```

# mdadm --examine /dev/sdx1
/dev/sdx1:
          Magic : a92b4efc
        Version : 1.2
[...bla bla bla...]
   Device Role : Active device 2
   Array State : AAAAAAA ('A' == active, '.' == missing, 'R' == replacing)

```

At this point you know, and this does not change, that the drive role 2 in your raid is fulfilled by the drive with the serial WD-WMAZA0602133. This is fixed. If the drive is not /dev/sdx but /dev/sdy the next time you boot, it's still the same. It does not change.

And device role 2 means, it's the 3rd drive in the array (counting starts at 0).

So in the Array State line above, it's:

```
   Array State : AAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
   Array State :   ^
```

In a mdadm failure message where you get some [UUUU] string, it's
```
[UU_UUUU]
   ^
```

this one. I.e. it's Array State : 0123456 or [0123456]. mdadm tells you not only the /dev/sdx name of the failed drive but also the role of the failed drive. So you always know, regardless of the name, which drive failed.

And my suggestion was, to make it easier to identify the failed drive physically, to put the drives in the same order in your computer case, according to their raid roles. So if you have a stack of HDDs in your big tower, you know the topmost is device 0, and the bottom most is device 6 or something. So if you get a mail about device role 3 failed, you don't even have to look at serial numbers anymore, you know exactly which to take.

> **XBNCPRk said:**
> nothing that says /dev/sdx is the one plugged into port y

If your /dev/sdx are random, you have to ignore it and rely on the raid device role instead. If that still does not help you, I'm sorry.

---

### Post by XBNCPRk on 2014-04-16
Thank you frost for your help, but again youre missing the point of my question. Im well aware of the roles and /dev/ labels. Im asking this: Does mdadm have a way to point you to a physical drive. The answer is NO, it does not. If there is a step in your method that relies on the user having maintained records, keeping lists, assuming correctly ordered drives and plugging or consulting a psychic, then you are missing the point of the question.
 
I do not have, nor wish to maintain lists of drive serials and roles for any number of friends servers that I helped them assemble because they are less tech savvy. 

> **frostschutz said:**
> 
You get the drive's serial number with hdparm or smartctl.


Again, thank you for the suggestion, but as I had stated, I was hoping to avoid the whole 'find the serial and start pulling drives until you find one that matches'. That is however apparently the best option at the moment so unless I can find anything else I'll mark this thread as closed.

---

