---
title: "Unexpected inconsistency error"
date: 2021-12-28
forum: General Help
---

### Post by sfksfk on 2021-12-28
Hi everyone,

have read through a lot of apparently similar reports around the forum, but the solutions for others did not make my problem go away.

Was using Ubuntu (18.04) normally when suddenly LibreOffice would not start. Tried the System Manager to manage the running processes - it did not open either, although Ubuntu apparently continued working as well as my browser. Shut down, went to lunch, after starting the laptop it did not boot Ubuntu, simply got stuck at the "Dell" sign that always appears when hitting the "start" button. Turned it off manually through the button, and when starting it again got the following message:

/dev/sda4: UNEXPECTED INCONSISTENCY: run fsck manually.
         (i.e without -a or -p options)
fsck exited with status code 4
The foot filesystem on /dev/sda4 requires a manual fsck.

After a few moments of desperation, looked up similar error reports online through my cell phone and executed fsck manually. It repaired a number of problems, I rebooted and everything seemed fine, but when I tried to start LibreOffice of System Manager they still do not open (browser working fine). Executed fsck again, found (and theoretically repaired) exactly the same errors concerning inodes and blocks. Rebooted, no error message and booted just fine, but LibreOffice and System Manager continue unable to work. Executed fsck, found and repaired the errors, executed it now again, told me that file system is clean, but the problem persists.

Any clue as to what might be happening? Thanks a lot in advance for your help.

SFK.

---

### Post by guiverc on 2021-12-28
If you're not aware of any causes; the issue is likely hardware related.

Depending on where you are; it can be caused by bad power (*something nearby that draws loads of current was switched on*) whilst your machine was already struggling (*it's hot thus cooling fans were on, drive(s) in use*) and you don't have a line-filter and as such unclean power causing glitches (*esp. if the PSU or power supply is getting old*).

Glitches in power can cause hardware components to *glitch* & the result is bad/corrupted data.  When the OS detects flawed data/corruption; a RW (*read-write*) file-system flips to RO (*read only*) which requires [manual] `fsck` or file-system checks to correct.

If the problem occurs once; you can write it off as a chance occurrence, but if it starts to re-occur that's a warning sign of *hardware failing*, but you need to check what.

I'd check
- RAM (*ramtests are easy & let it run through many times overnight or better a day + night*)
- PSU (*they produce less power as they age, and if not providing enough reliable power even good components misbehave*, *check you're not drawing more power than it can provide*)
- disk drive(s)  (*using drive's inbuilt SMART tools; [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) doing it from live media*)
- motherboard scan (*remove fluff etc. & scan for swollen caps etc*).

From your description - I'd look at your hardware.

---

### Post by sfksfk on 2021-12-28
Hi guiverc,

thanks a lot for your fast and complete reply. I tested RAM with memtester and everything seems fine. So I installed gsmartcontrol and ran a simple smartctl command, obtaining the following output, which I am not competent to interpret (I copied and pasted only what appears to be most important to so keep it relatively short, but can obviously add info if it could help an assessment).

SMART Attributes Data Structure revision number: 128
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate      0x000b   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time                    0x0027   100   100   001    Pre-fail  Always       -       1796
  5 Reallocated_Sector_Ct       0x0033   100   100   050    Pre-fail  Always       -       0
  9 Power_On_Hours               0x0032   066   066   000    Old_age   Always       -       13801
 12 Power_Cycle_Count          0x0032   100   100   000    Old_age   Always       -       6757
191 G-Sense_Error_Rate        0x0032   100   100   000    Old_age   Always       -       177
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       210
193 Load_Cycle_Count           0x0032   095   095   000    Old_age   Always       -       50103
194 Temperature_Celsius        0x0022   100   100   000    Old_age   Always       -       35 (Min/Max 16/44)
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       82415543
200 Multi_Zone_Error_Rate    0x0032   100   100   000    Old_age   Always       -       267678260
240 Head_Flying_Hours          0x0032   068   068   000    Old_age   Always       -       13199
241 Total_LBAs_Written          0x0032   100   100   000    Old_age   Always       -       13632194357
242 Total_LBAs_Read             0x0032   100   100   000    Old_age   Always       -       19045990901
254 Free_Fall_Sensor             0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 37 (device log contains only the most recent five errors)
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

Error 37 occurred at disk power-on lifetime: 13801 hours (575 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 c0 38 09 1a 40  Error: UNC at LBA = 0x001a0938 = 1706296

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 f8 50 dd 79 40 00      01:10:28.590  READ FPDMA QUEUED
  60 08 60 90 d6 79 40 00      01:10:28.590  READ FPDMA QUEUED
  60 08 b8 28 dd 79 40 00      01:10:28.590  READ FPDMA QUEUED
  60 08 58 88 d6 79 40 00      01:10:28.590  READ FPDMA QUEUED
  60 08 50 80 d6 79 40 00      01:10:28.583  READ FPDMA QUEUED

Would be thankful for further help considering the serious limitations of my knowledge when it comes to these aspects.

Best wishes.

SFK.

---

### Post by sfksfk on 2022-01-22
Hi everyone,

sorry to bother you again, but although my laptop seems to be working fine all around, everytime I launch LibreOffice the problem reappears. Can anyone tell me if the data above shows sings of hard disk failure? I would like to know if buying a new HD (or even better, switching it for an SSD) could solve the issues.

Thanks again.

SFK.

---

### Post by Impavidus on 2022-01-23
SMART data are easiest to interpreted if you monitor them over time. On my laptop I've monitored it for the past 3 years and found that the reallocated sector count steadily increased from 175 to 211. The hard drive is old (about 10 years), but still has some life left. I make sure I've got good backups, but haven't experience file damage yet.

Some of your numbers may be bogus, as they are very low or very high, and some numbers are missing (current_pending_sector could be interesting). Other than that, it looks like an old hard drive, not necessarily broken, but it could be. Your symptoms suggest a hard drive problem, so a new drive may help. An SSD would make the computer perform better than ever before, so you could consider that if there's enough life left in the rest of your computer to warrant such an investment.

---

### Post by couzin2000 on 2022-03-15
> **guiverc said:**
> If you're not aware of any causes; the issue is likely hardware related.

Depending on where you are; it can be caused by bad power (*something nearby that draws loads of current was switched on*) whilst your machine was already struggling (*it's hot thus cooling fans were on, drive(s) in use*) and you don't have a line-filter and as such unclean power causing glitches (*esp. if the PSU or power supply is getting old*).

Glitches in power can cause hardware components to *glitch* & the result is bad/corrupted data.  When the OS detects flawed data/corruption; a RW (*read-write*) file-system flips to RO (*read only*) which requires [manual] `fsck` or file-system checks to correct.

If the problem occurs once; you can write it off as a chance occurrence, but if it starts to re-occur that's a warning sign of *hardware failing*, but you need to check what.

I'd check
- RAM (*ramtests are easy & let it run through many times overnight or better a day + night*)
- PSU (*they produce less power as they age, and if not providing enough reliable power even good components misbehave*, *check you're not drawing more power than it can provide*)
- disk drive(s)  (*using drive's inbuilt SMART tools; [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools) doing it from live media*)
- motherboard scan (*remove fluff etc. & scan for swollen caps etc*).

From your description - I'd look at your hardware.

Thank you. 
I was able to use a USB flash drive with Ubuntu Live 21.xx on it to run on my PC. I unmounted my root drive (which is a RAID1 array, found its name in [FONT=Courier New]/etc/fstab[/FONT]) by using [FONT=Courier New]sudo umount[/FONT].
Then ran [FONT=Courier New]sudo fsck /dev/blablabla[/FONT]. The application ran a play-by-play of everything that was outta whack. From what I understood here, it felt like someking of write operation had been set to be recorded from one place to the next, perhaps an update of somekind. However the reboot operation didn't work properly and just went too fast, preventing the full data commit. This might be what cause the errors. 
After fsck ran trhough everything, I just rebooted. The PC is now working correctly.

However, afetr this incident, I may end up using something different that Ubuntu for that PC. It's a server, but I run into too many problems with this, and may just install Unraid on the server. 

Thanks again for all the help!

---

