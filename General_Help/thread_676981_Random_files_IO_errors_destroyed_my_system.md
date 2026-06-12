---
title: "Random files I/O errors destroyed my system"
date: 2008-01-24
forum: General Help
---

### Post by Sam on 2008-01-24
Ok... This time it's serious. My work PC has crashed yesterday. I was working like usual. I tried to mkdir during the day and it showed "mkdir not installed, install coreutils bla bla'. At this moment, I told myself "ok this is a small issue, will check this later". And later, X suddenly crashed. Kernel panic. SysReq keys pressed.

During reboot, I've got a lot of error messages. X failed to start. Tried to login with my user on a TTY, no way. Hopefully I've enabled the root account, and I've managed to get logged in my system. Almost everything was buggy. In fact, a lot of system bin/libs where unavailable. So I rebooted with a live CD.

I've attached a screenshot with the listing of /bin and /sbin. Note the "ERROR: cannot open 'bin/mkdir' (Input/output error)" when accessing a "erroneous" file.

Then I made a fsck.```
root@ubuntu:/mnt# e2fsck -v /dev/hda1
e2fsck 1.40-WIP (14-Nov-2006)
/ has been mounted 32 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 130305 has zero dtime.  Fix<y>? yes

Deleted inode 211937 has zero dtime.  Fix<y>? yes

Deleted inode 359073 has zero dtime.  Fix<y>? yes

Deleted inode 621153 has zero dtime.  Fix<y>? yes

Deleted inode 621857 has zero dtime.  Fix<y>? yes

<snip>

Deleted inode 847841 has zero dtime.  Fix<y>? yes

Deleted inode 944833 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Entry '100baset_hub.shape' in /usr/share/dia/shapes/Cisco (18649) has deleted/unused inode 833480.  Clear<y>? yes

Entry '1000.png' in /usr/share/dia/shapes/Cisco (18649) has deleted/unused inode 833479.  Clear<y>? yes

Entry '100baset_hub.png' in /usr/share/dia/shapes/Cisco (18649) has deleted/unused inode 833481.  Clear<y>? yes

Entry '10700.shape' in /usr/share/dia/shapes/Cisco (18649) has deleted/unused inode 833482.  Clear<y>? yes

Entry '10700.png' in /usr/share/dia/shapes/Cisco (18649) has deleted/unused inode 833483.  Clear<y>? yes

<snip>

Entry '..' in ??? (946205) has deleted/unused inode 944840.  Clear<y>? yes

Entry '..' in ??? (946215) has deleted/unused inode 944840.  Clear<y>? yes

<snip>

Entry 'mkdir' in /bin (749249) has deleted/unused inode 755124.  Clear<y>? yes

Entry 'mknod' in /bin (749249) has deleted/unused inode 755125.  Clear<y>? yes

Entry 'pwd' in /bin (749249) has deleted/unused inode 755127.  Clear<y>? yes

Entry 'readlink' in /bin (749249) has deleted/unused inode 755128.  Clear<y>? yes

<snip>

Pass 3: Checking directory connectivity
Unconnected directory inode 635574 (...)
Connect to /lost+found<y>? yes

Unconnected directory inode 635586 (...)
Connect to /lost+found<y>? yes

Unconnected directory inode 635598 (...)
Connect to /lost+found<y>? yes

<snip>

Pass 4: Checking reference counts
Unattached inode 98168
Connect to /lost+found<y>? yes

Inode 98168 ref count is 2, should be 1.  Fix<y>? yes

Unattached inode 98170
Connect to /lost+found<y>? yes

Inode 98170 ref count is 2, should be 1.  Fix<y>? yes

<snip>

Pass 5: Checking group summary information
Block bitmap differences:  -(86918--86967) -(140101--140116) -140119 -262734 -262891 -(270349--270353) -(270450--270452) -(273153--273164) -(273229--273234) -(273521--273527) -(274169--274224) -(274228--274249) -(274260--274348) -(274371--274374) -(274420--274441) -(275953--275996) -(276246--276481) -276484 -276486 -(276488--276634) -(276639--276758) -(276760--276997) -(277042--277062) -(277066--277068) -(277087--277518) -(278876--278879) -280583 -280585 -(282682--282687) -282726 -(282771--283322) -(283325--283331) -289168 -292947 -295449 -(433860--433902) -(433917--433928) -(433934--433936) -(433975--433982) -(441785--441820) -(525710--525713) -(550066--550067) -(591036--591128) -725237 -(725278--725279) -727087 -727219 -(727960--727961) -729097 -(729135--729136) -729138 -729213 -729220 -729536 -729542 -729545 -729569 -729783 -730312 -733249 -733675 -735236 -(735280--735282) -735395 -735402 -739335 -(739413--739415) -(739417--739423) -739592 -739615 -739688 -741129 -(741369--741374) -(741419--741421) -(741516--741519) -(741618--741619) -741695 -741795 -743479 -743498 -744072 -(744085--744086) -(744147--744148) -(744179--744217) -(744317--744364) -745923 -746473 -746475 -746481 -746586 -747071 -747229 -747231 -(747329--747332) -747335 -747354 -747427 -(747474--747477) -(747522--747523) -(747993--748001) -(748003--748004) -748100 -(748110--748112) -(748126--748127) -(748133--748134) -748139 -748141 -(748147--748149) -(748248--748258) -(748261--748288) -(748290--748291) -748293 -748295 -748299 -(748301--748333) -(748376--748387) -748396 -(748407--748420) -(748422--748423) -(748560--748575) -(748649--748652) -(748673--748675) -(748721--748731) -(748733--748734) -748736 -748739 -(748742--748744) -(748893--748896) -748953 -748955 -748977 -748986 -748992 -748995 -748997 -748999 -749120 -749130 -(749146--749147) -(749480--749487) -(749489--749491) -749493 -749495 -(749497--749498) -(749503--749507) -(749509--749510) -749517 -(749520--749544) -(749552--749567) -749575 -749583 -749847 -749891 -(749893--749898) -(749900--749903) -(749908--749911) -750045 -750393 -750914 -(751030--751031) -752152 -(752172--752175) -(752178--752180) -752274 -(752297--752302) -752304 -(752307--752311) -752358 -752386 -752411 -752478 -752534 -(752588--752592) -752623 -(752662--752665) -(754265--754286) -(754288--754305) -754308 -(754335--754339) -754344 -(754378--754379) -754386 -754392 -(754460--754463) -(754703--754706) -(754718--754719) -(755962--755967) -756505 -(756633--756643) -756647 -756728 -757899 -758565 -759243 -766602 -(767006--767007) -(767071--767075) -(767116--767125) -(767134--767135) -(767488--767512) -(767514--767682) -(767840--767863) -(767868--767893) -767984 -768010 -(768016--768018) -768312 -(768320--768327) -(768346--768351) -(768480--768509) -(768512--768549) -768983 -(769288--769316) -772615 -(772721--772727) -772729 -(772732--772735) -(772965--772967) -(774797--774806) -(775037--775039) -(775319--775344) -(775384--775546) -783595 -(812048--812052) -(812062--812063) -826283 -(826285--826287) -(826413--826460) -(826464--826524) -(1252635--1252640) -(1259293--1259310) -1259525 -1259527 -(1259537--1259541) -(1260257--1260277) -(1263759--1263760) -1264511 -(1266619--1266620) -(1268396--1268417) -(1269245--1269246) -1270095 -(1270385--1270387) -(1271033--1271037) -1276180 -(1279271--1279325) -(1282774--1282893) -1283072 -(1283075--1283076) -1283774 -(1283862--1283876) -(1284007--1284010) -(1284075--1284112) -(1284123--1284175) -(1284278--1284314) -(1284317--1284346) -(1284688--1284701) -(1284712--1284716) -(1284740--1284750) -(1285467--1285841) -(1285859--1285868) -(1286096--1286098) -(1286432--1286433) -1290384 -1290421 -1290457 -1290472 -(1291288--1291289) -1291408 -(1291824--1291827) -(1291829--1291835) -(1291838--1291840) -(1291846--1291848) -(1291854--1291856) -(1291862--1291864) -(1291868--1291906) -(1300324--1300368) -(1301043--1301141) -(1301144--1301146) -(1301163--1301168) -(1301171--1301172) -(1301178--1301179) -(1301182--1301198) -(1301237--1301250) -(1301510--1301511) -1305099 -(1316272--1316273) -1316313 -(1319645--1319646) -(1320290--1320297) -1327325 -1330247 -1347635 -1348339 -(1353961--1353968) -(1354518--1354525) -(1354527--1354528) -1354534 -1354543 -1366622 -(1369575--1369576) -1372606 -1372616 -1372626 -(1372636--1372637) -1372805 -(1373214--1373230) -(1374969--1374972) -1374994 -(1375690--1375693) -(1375830--1375831) -(1378614--1378621) -(1393378--1393386) -1400618 -(1404124--1404127) -(1404137--1404138) -(1404901--1404903) -(1404949--1404958) -1404961 -1408654 -1418243 -(1425347--1425348) -(1425356--1425380) -(1425467--1425468) -1430684 -(1430794--1430798) -(1430963--1430964) -(1481306--1481308) -(1481391--1481393) -1482278 -1482401 -(1484872--1484873) -(1484884--1484892) -(1485446--1485448) -(1509397--1509401) -(1509864--1509865) -(1511485--1511486) -(1511522--1511536) -(1513014--1513018) -1515522 -(1515703--1515705) -(1517616--1517619) -(1523386--1523400) -(1523768--1523771) -(1525438--1525455) -1525457 -(1526930--1526931) -(1530966--1530968) -(1531039--1531040) -(1534046--1534048) -(1536000--1536008) -(1536066--1536071) -(1538393--1538396) -(1538398--1538401) -(1538636--1538639) -(1542176--1542191) -(1542535--1542571) -(1542593--1542603) -(1542621--1542630) -(1542640--1542692) -(1553946--1553950) -(1554557--1554565) -1557033 -(1575772--1575773) -(1577105--1577106) -(1577108--1577110) -(1577114--1577117) -1577127 -1577129 -(1577131--1577133) -(1577135--1577136) -(1579008--1579011) -1579492 -1581251 -(1582375--1582376) -(1582378--1582379) -(1582389--1582392) -(1591297--1591298) -1591332 -(1595393--1595394) -(1595401--1595404) -1599488 -1599490 -1602978 -(1603585--1603586) -1603588 -1617049 -1617542 -(1640183--1640191) -1656890 -1656996 -1657011 -1657015y -1657063 -1658734 -(1658880--1658882) -1658884 -(1658886--1658892) -(1673100--1673105) -(1675120--1675122) -1678149 -1687780 -(1687782--1687784) -(1687786--1687788) -1687791 -(1687793--1687794) -(1687873--1687874) -(1687876--1687879) -(1688019--1688022) -1703266 -(1703268--1703296) -(1725822--1725828) -(1736168--1736170) -1736172 -(1736305--1736316) -(1738290--1738325)yy -(1738374--1738451) -1788530 -1788532 -1788534 -1788536 -1788538 -1788540 -(1788637--1788646) -1818134 -(1822855--1822856) -(1826463--1826470) -(1826669--1826673) -(1826890--1826910) -(1835666--1835667) -(1835669--1835695) -(1837855--1837907) -1843003 -1843621 -(1845536--1845539) -1845551 -1853051 -(1854592--1854596) -(1854598--1854599) -1857412 -(1888889--1888895) -(1912832--1912833) -(1912837--1912844) -(1913718--1913719) -(1916995--1917001) -(1918998--1918999) -(1921444--1921493) -1931359 -1931363 -(1936120--1936124) -(1936129--1936136) -(1936546--1936554)
Fix<y>? yes

Free blocks count wrong for group #2 (4, counted=54).
Fix<y>? yes

Free blocks count wrong for group #4 (595, counted=612).
Fix<y>? yes

<snip>

***** FILE SYSTEM WAS MODIFIED *****

  227933 inodes used (23.32%)
    8102 non-contiguous inodes (3.6%)
         # of inodes with ind/dind/tind blocks: 15269/152/0
 1664224 blocks used (85.17%)
       0 bad blocks
       0 large files

  187014 regular files
   18095 directories
    1226 character device files
    4547 block device files
       5 fifos
     462 links
   16967 symbolic links (15213 fast symbolic links)
      73 sockets
--------
  227589 files
```



After this, a lot of files where put in /lost+found

Hopefully, my home directory is located in an another partition, which is ok (I've made a backup immediately after the crash).


The harddrive was bought last year. It's a Western Digital.
I'm running Feisty.


So what are you opinions ? Hard drive failure (although it makes no suspect noise and it worked like a charm some hours before the failure) ?

I'm already thinking of reinstalling the whole system. But if these are typical symptoms of a hard disk failure I'll buy a new one before. Or have you any idea how to restore it ?

Please tell me what do you think !

---

### Post by glauco.b on 2008-01-24
It doesn't seem to be a hard disk failure

I guess it is a file system failure, maybe a software crash during a system shutdown or something similar.

In the lost+found folder you'll find whatever the system was able to recover after the failure, even incomplete files.

I believe that in this case, if your system is non functional, you should backup your data and reinstall.

---

### Post by Sam on 2008-01-24
The system was always shut down properly... And I paid attention to get it as clean as possible.

Can anyone explain how a filesystem can fail like this (btw I'm using ext3) ? If it was just a file or something I'm working on it's ok, but a bunch of files everywhere ?? and a lot of system binaries ???

---

### Post by chrisccoulson on 2008-01-24
This definately does sound like hard drive failure. I recently had a WD drive fail on me. If you bought it last year, you can RMA it back to WD and they'll give you a new one. You should have a 5 year warranty with it.

---

### Post by Zwack on 2008-01-24
> **Sam said:**
> 
After this, a lot of files where put in /lost+found

The harddrive was bought last year. It's a Western Digital.


Files are put in /lost+found if fsck finds them lying around on the hard drive.  If you can't identify them then you can delete them...

I've had bad luck with Western Digital drives but it might not be a drive failure.  If you've backed everything up and can afford to do this then wipe the drive and run badblocks on it...

If it turns up clean then it was possibly an unusual file system error that has trashed the directory structure.  If not then you have either a media error, or a hard drive failure.

Z.

---

### Post by Sam on 2008-01-24
Ok, thank you all for your replies.

> **Zwack said:**
> Files are put in /lost+found if fsck finds them lying around on the hard drive.  If you can't identify them then you can delete them...

I've had bad luck with Western Digital drives but it might not be a drive failure.  If you've backed everything up and can afford to do this then wipe the drive and run badblocks on it...

If it turns up clean then it was possibly an unusual file system error that has trashed the directory structure.  If not then you have either a media error, or a hard drive failure.

Z.

```
root@ubuntu:~# badblocks -v /dev/hda1
Checking blocks 0 to 7815590
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.
```

That sounds great... No need to buy a new drive !

I will reinstall the system on the same partition. Thanks for your help !


(I hope this kind of filesystem failure don't happen too often...)

---

### Post by Zwack on 2008-01-24
> **Sam said:**
> Ok, thank you all for your replies.

I will reinstall the system on the same partition. Thanks for your help !


(I hope this kind of filesystem failure don't happen too often...)

If it happens again try running dmesg as soon as it happens and seeing if there are any errors listed in the end of the kernel logs.  That might help pinpoint the actual problem.  

Without knowing what broke it's very hard to say how to fix it, but it could be almost anything... It could be a hard drive failure, or a media failure (seems unlikely if badblocks says it's clean) It could be a filesystem issue but again it seems odd that you're the only one who has tickled that bug.  It could have been a badly behaved application that tried writing in the wrong location.  It could even be a memory fault that caused it... 

So, next time check the files in /var/log and run dmesg to see if you can find anything.  I hope that there isn't a next time.

Z.

---

### Post by articpenguin on 2008-01-24
> **Sam said:**
> Ok, thank you all for your replies.



```
root@ubuntu:~# badblocks -v /dev/hda1
Checking blocks 0 to 7815590
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.
```

That sounds great... No need to buy a new drive !

I will reinstall the system on the same partition. Thanks for your help !


(I hope this kind of filesystem failure don't happen too often...)

modern hard disks hide bad sectors. When they find bad ones they relocate it to a spare sector.

---

### Post by chrisccoulson on 2008-01-24
Yes, badblocks told me I didn't have bad blocks on my failed disk, after my machine crashed and I got a kernel panic on subsequent boots. But when I ran the Western Digital diagnostic tool, it told me the SMART status was bad, so I sent it back to WD and got a replacement.

The filesystem corruption has to be triggered by something - it shouldn't just 'happen' (else that would be a Critical bug). I've never seen this level of filesystem corruption without some sort of hardware failure.

---

### Post by Zwack on 2008-01-24
> **chrisccoulson said:**
> Yes, badblocks told me I didn't have bad blocks on my failed disk, after my machine crashed and I got a kernel panic on subsequent boots. But when I ran the Western Digital diagnostic tool, it told me the SMART status was bad, so I sent it back to WD and got a replacement.

The filesystem corruption has to be triggered by something - it shouldn't just 'happen' (else that would be a Critical bug). I've never seen this level of filesystem corruption without some sort of hardware failure.

Hey, I didn't say that it just happened... I said that without any other information I can't guess at what happened.  I was assuming that badblocks would be run on the entire drive not just /dev/hda1.   Is there a command line way to probe a drive for relocation information?  If so then that is something else that should be looked at.

As for not seeing this level of filesystem corruption without a hardware failure...  This could be the result of a write to the disk that becomes a write to a different part of the disk by a memory fault (still a hardware issue, but not a disk fault).

I've seen servers crash because they weren't being used enough before (certain SUN servers in 2000 would crash because the memory wasn't being exercised sufficiently) which is very odd behaviour, and not a cause that you would have predicted. 

Z.

---

### Post by Zwack on 2008-01-24
> **articpenguin said:**
> modern hard disks hide bad sectors. When they find bad ones they relocate it to a spare sector.

Same goes for old ones in some cases...

Two points:- 

1) if the drive suffered a failure in one sector and replaced it with a good sector from it's "spare" list then is the drive safe to use or not?  At what point is it no longer safe to use?  If this was a single unfortunate sector that got corrupted then this could well be perfectly safe to use and potentially for a very long time.

2) If there are lots of these errors then the "relocation space" will run out.  How do you detect such a situation?  I guess, as an old curmudgeon, I don't trust machines to handle this for me unless I know it has some way of saying "I need help".  

Z.

---

### Post by articpenguin on 2008-01-24
> **Zwack said:**
> Same goes for old ones in some cases...

Two points:- 

1) if the drive suffered a failure in one sector and replaced it with a good sector from it's "spare" list then is the drive safe to use or not?  At what point is it no longer safe to use?  If this was a single unfortunate sector that got corrupted then this could well be perfectly safe to use and potentially for a very long time.

2) If there are lots of these errors then the "relocation space" will run out.  How do you detect such a situation?  I guess, as an old curmudgeon, I don't trust machines to handle this for me unless I know it has some way of saying "I need help".  

Z.

A modern hard drive comes with many spare sectors. When a sector is found to be bad by the firmware of a disk controller, the disk controller remaps the logical sector to a different physical sector. In the normal operation of a hard drive, the detection and remapping of bad sectors should take place in a manner transparent to the rest of the system. When the operating system begins to detect bad sectors, in most cases, it means that the surface of the hard disk is failing and the drive has run out of spare sectors with which to remap the failed sector.

---

### Post by articpenguin on 2008-01-24
> **articpenguin said:**
> A modern hard drive comes with many spare sectors. When a sector is found to be bad by the firmware of a disk controller, the disk controller remaps the logical sector to a different physical sector. In the normal operation of a hard drive, the detection and remapping of bad sectors should take place in a manner transparent to the rest of the system. When the operating system begins to detect bad sectors, in most cases, it means that the surface of the hard disk is failing and the drive has run out of spare sectors with which to remap the failed sector.


[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

i meant to edit and the add url to my last post

---

### Post by Sam on 2008-01-24
This is the result of smartctl on the drive:

```
root@gv01:~# smartctl --all /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE family
Device Model:     WDC WD1600JB-00REA0
Serial Number:    WD-WCANMA308406
Firmware Version: 20.00K20
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jan 25 00:43:18 2008 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (4980) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  60) minutes.
Conveyance self-test routine
recommended polling time:        (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   185   185   021    Pre-fail  Always       -       3716
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       252
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2834
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       252
194 Temperature_Celsius     0x0022   105   101   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       5
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       5
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   200   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 7 (device log contains only the most recent five errors)
        CR = Command Register [HEX]
        FR = Features Register [HEX]
        SC = Sector Count Register [HEX]
        SN = Sector Number Register [HEX]
        CL = Cylinder Low Register [HEX]
        CH = Cylinder High Register [HEX]
        DH = Device/Head Register [HEX]
        DC = Device Command Register [HEX]
        ER = Error register [HEX]
        ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 7 occurred at disk power-on lifetime: 2806 hours (116 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7b bb e2 e0  Error: UNC 8 sectors at LBA = 0x00e2bb7b = 14859131

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 7b bb e2 04 58   1d+05:16:12.990  READ DMA EXT
  25 00 58 03 ea e2 04 58   1d+05:16:12.980  READ DMA EXT
  25 00 08 db e1 e2 04 58   1d+05:16:12.980  READ DMA EXT
  25 00 10 c3 e1 e2 04 58   1d+05:16:12.980  READ DMA EXT
  25 00 08 83 e1 e2 04 58   1d+05:16:12.980  READ DMA EXT

Error 6 occurred at disk power-on lifetime: 2806 hours (116 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 30 7b bb e2 e0  Error: UNC 48 sectors at LBA = 0x00e2bb7b = 14859131

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 30 7b bb e2 04 58   1d+05:16:10.250  READ DMA EXT
  25 00 38 73 bb e2 04 58   1d+05:16:07.525  READ DMA EXT
  35 00 a0 7d aa ee 00 58   1d+05:16:07.525  WRITE DMA EXT
  35 00 a0 05 a5 ee 00 58   1d+05:16:07.520  WRITE DMA EXT
  25 00 38 fb ba e2 04 58   1d+05:16:05.120  READ DMA EXT

Error 5 occurred at disk power-on lifetime: 2806 hours (116 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 38 73 bb e2 e0  Error: UNC 56 sectors at LBA = 0x00e2bb73 = 14859123

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 38 73 bb e2 04 58   1d+05:16:07.525  READ DMA EXT
  35 00 a0 7d aa ee 00 58   1d+05:16:07.525  WRITE DMA EXT
  35 00 a0 05 a5 ee 00 58   1d+05:16:07.520  WRITE DMA EXT
  25 00 38 fb ba e2 04 58   1d+05:16:05.120  READ DMA EXT
  25 00 c8 bb b9 e2 04 58   1d+05:16:05.115  READ DMA EXT

Error 4 occurred at disk power-on lifetime: 2567 hours (106 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7b bb e2 e0  Error: UNC 8 sectors at LBA = 0x00e2bb7b = 14859131

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 7b bb e2 04 58   4d+11:08:12.965  READ DMA EXT
  35 00 08 33 21 f3 0d 58   4d+11:08:12.965  WRITE DMA EXT
  35 00 10 c3 20 f3 0d 58   4d+11:08:12.965  WRITE DMA EXT
  35 00 08 5b 21 ab 0a 58   4d+11:08:12.965  WRITE DMA EXT
  35 00 10 c3 20 ab 0a 58   4d+11:08:12.965  WRITE DMA EXT

Error 3 occurred at disk power-on lifetime: 2567 hours (106 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 7b bb e2 e0  Error: UNC 8 sectors at LBA = 0x00e2bb7b = 14859131

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 7b bb e2 04 58   4d+11:08:10.220  READ DMA EXT
  35 00 28 07 63 b8 00 58   4d+11:08:10.220  WRITE DMA EXT
  35 00 30 ef 5e b8 00 58   4d+11:08:10.220  WRITE DMA EXT
  35 00 38 af 5e b8 00 58   4d+11:08:10.220  WRITE DMA EXT
  35 00 38 6f 5e b8 00 58   4d+11:08:10.220  WRITE DMA EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

The drive has run for 2834 hours. 
There are three errors which occured at 2806 hours, this may match with the failure.

Seems a bit crypty for me... Anyone has an idea ? Thanks in advance.

---

### Post by Zwack on 2008-01-25
> **Sam said:**
> This is the result of smartctl on the drive:
...

The drive has run for 2834 hours. 
There are three errors which occured at 2806 hours, this may match with the failure.

Seems a bit crypty for me... Anyone has an idea ? Thanks in advance.

UNC X sectors means that there was an uncorrectable error of X sectors 

From the Smartmontools FAQ...

> # My ATA drive is failing its self-tests, but its SMART health status is 'PASS'. What's going on?

If your ATA drive supports self-tests, you should run them on a regular basis, for example one per week:
smartctl -t long /dev/hd?
After the test has completed, you should examine the results with:
smartctl -l selftest /dev/hd?

If the drive fails a self-test, but still has 'PASS' SMART health status, this usually means that there is a corrupted (uncorrectable=UNC) sector on the disk. This means that the ECC data stored at that sector is not consistent with the user data stored at that sector, and an attempt to read the sector fails with a UNC error. This can be a one-time transient effect: a sudden power failure while the disk was writing to the sector corrupted the ECC code or data, but the sector could correctly store new data. Or it can be a permanent effect: the magnetic media has been damaged by a bit of dust, and the sector could not correctly store new data.

If the disk can read the sector of data a single time, and the damage is permanent, not transient, then the disk firmware will mark the sector as 'bad' and allocate a spare sector to replace it. But if the disk can't read the sector even once, then it won't reallocate the sector, in hopes of being able, at some time in the future, to read the data from it. A write to an unreadable (corrupted) sector will fix the problem. If the damage is transient, then new consistent data will be written to the sector. If the damange is permanent, then the write will force sector reallocation. Please see Bad block HOWTO for instructions about how to force this sector to reallocate (Linux only).

The disk still has passing health status because the firmware has not found other signs of trouble, such as a failing servo.

Such disks can often be repaired by using the disk manufaturer's 'disk evaluation and repair' utility. Beware: this may force reallocation of the lost sector and thus corrupt or destroy any file system on the disk. See Bad block HOWTO for generic Linux instructions.


I hope that this helps.  

Z.

---

### Post by Sam on 2008-01-25
Ok this is an interesting reading...

Thanks for helping ! ;)

---

### Post by ahurtt on 2008-01-30
I ran into something similar to this yesterday.  On booting I had all the same kind of similar file system problems.  The hard drive is practically brand new.  Bought it a couple months ago for a repair job but ended up not needing it and decided to keep it anyway.  So I just installed it into my own system a few days ago.  It was sitting on the shelf up until then.  I have never had a hard drive go bad that fast.  That is why I doubt it is the drive that is the problem.  The only thing I can say that is different from what I usually do is that this boot up came after I had put the system in Hibernate rather than just shutting down like normal.  I think I'll just avoid doing that from now on in case that is the cause.

I am on the latest Kubuntu Gutsy Gibbon for AMD 64.  I have an AMD 64 x2 dual core.
I don't know if it matters but, it is a 160 Gig IDE drive petitioned as:
/ mounted on 10 Gig primary partition using ext3 at beginning of drive.
swap mounted 3 Gig at end of drive
/home mounted as primary partition on the middle part (the rest) using ext3.

After this happened I decided to just nuke it all and reinstall fresh.

I'm trying to like this whole open source and Linux thing but between this problem and the one I experienced with the adept package manager not being able to commit package changes. . .It seems like I have spent more time figuring out how to resolve problems than I have spent learning to just use Kubuntu Linux.  Though I guess in a way that is learning as well. . .

Is there a way to remove Hibernate as one of the available options you get when you click to logoff in KDE?  I don't want to accidentally click it again until I figure out more about this.

---

