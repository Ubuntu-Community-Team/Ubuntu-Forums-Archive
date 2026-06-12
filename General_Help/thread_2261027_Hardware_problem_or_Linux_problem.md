---
title: "Hardware problem or Linux problem?"
date: 2015-01-15
forum: General Help
---

### Post by dpilot83 on 2015-01-15
Hi all. I'm about to pull my hair out here.

Windows 7 was throwing BSOD's making the machine unusable. I used Linux LiveCD (and later LiveUSB) to try and get stuff more thoroughly backed up before re-installing Windows.

Both LiveCD and LiveUSB were incredibly slow and froze regularly to the point that they were not acceptable for fixing the problem. Fortunately the HD had an empty partition on it so I just installed Windows 7 to that partition to back the last few things up before re-installing on the correct partition.

I updated BIOS and installed Windows 7 and all updated drivers and software. Working better than it has ever worked before. But the slow/buggy LiveCD and LiveUSB was still bothering me.

Started looking into it and learned that slow LiveCD could actually be a sign of a failing hard drive which made no sense to me but I decided to physically disconnect the HD from the motherboard and power supply and try again.

At this point the LiveCD is now lightning fast for whatever reason but it still freezes after perhaps 10 minutes of use.

I ran memtest86+ on it for over 12 hours (21 passes) and it found no errors. When it fails the CPU temps are below 50C.

I also ran the check on the LiveCD to verify the integrity of the LiveCD and it passed.

Is my hard drive bad or going bad since LiveCD performance drastically improved when the hard drive was disconnected from the system? Or is there something else wrong since the LiveCD still freezes when the hard drive is disconnected? Or perhaps the freezing is related to a Linux problem rather than a hardware problem since Windows 7 seems to work fine now for hours on end?

I am so confused. Any help would really be appreciated. Thanks.

---

### Post by grahammechanical on 2015-01-15
Are you really using Ubuntu 7.10? My first Ubuntu install was 7.04 and I tried to install it again the other week. I could not get a live session to run. Then I remembered that I had upgraded the video adapter. It is likely that I am using a video card that did not exist when 7.04 was released. So, that live session does not have a driver from my new video card.

If you are using 7.10 and your hardware was released after 7.10 was released, then I would not be surprised if there were difficulties running the live session.

Regards.

---

### Post by dpilot83 on 2015-01-15
Sorry, I haven't been on the forums in a long time. I'll update my signature.

In the meantime, this is a desktop machine built by a local computer place in 2010. It has an MSI Motherboard (P55-53), 1156 socket i5-750 Mhz processor, 4 GB of RAM and an MSI nVidia graphics card (GT240?). Also a 320 GB 7200 RPM SATA hard drive. I'm using Ubuntu 14.04 for the LiveCD.

---

### Post by Yellow Pasque on 2015-01-15
It does sort of sound like a bad hard disk. Try to get the SMART information for the hard disk.
```
sudo apt-get install smartmontools
sudo smartmontools -q noserial -a /dev/sda   #assuming your hard disk is /dev/sda
```

---

### Post by dpilot83 on 2015-01-16
Thanks. I could not get the LiveUSB to last long enough to install smartmontools and I'm not totally sure how that works but I assume you cannot install smartmontools (even temporarily into system memory) using the LiveCD (and I don't think I could have gotten the LiveCD to last that long either actually) so I installed the Windows version since for whatever reason, Windows seems to be working fine.

Windows installed a shortcut in the start menu to the -x option first so I just ran that first. Here are the results of that:

```
smartctl -x sda

smartctl 6.3 2014-07-26 r3976 [x86_64-w64-mingw32-win7-sp1] (sf-6.3-1)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3320613AS
Serial Number:    9SZ6TLSF
LU WWN Device Id: 5 000c50 0206031d8
Firmware Version: CC2J
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Jan 15 23:05:05 2015 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM level is:     208 (intermediate), recommended: 208
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, frozen [SEC2]
Wt Cache Reorder: Unknown

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
data collection:                (  617) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp
ort.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  69) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR--   114   099   006    -    82236688
  3 Spin_Up_Time            PO----   100   097   000    -    0
  4 Start_Stop_Count        -O--CK   099   099   020    -    1547
  5 Reallocated_Sector_Ct   PO--CK   100   100   036    -    0
  7 Seek_Error_Rate         POSR--   078   060   030    -    69962218
  9 Power_On_Hours          -O--CK   087   087   000    -    12019
 10 Spin_Retry_Count        PO--C-   100   100   097    -    0
 12 Power_Cycle_Count       -O--CK   100   100   020    -    560
184 End-to-End_Error        -O--CK   100   100   099    -    0
187 Reported_Uncorrect      -O--CK   100   100   000    -    0
188 Command_Timeout         -O--CK   100   099   000    -    3
189 High_Fly_Writes         -O-RCK   092   092   000    -    8
190 Airflow_Temperature_Cel -O---K   075   063   045    -    25 (Min/Max 21/25)
194 Temperature_Celsius     -O---K   025   040   000    -    25 (0 11 0 0 0)
195 Hardware_ECC_Recovered  -O-RC-   057   041   000    -    82236688
197 Current_Pending_Sector  -O--C-   100   100   000    -    0
198 Offline_Uncorrectable   ----C-   100   100   000    -    0
199 UDMA_CRC_Error_Count    -OSRCK   200   200   000    -    1
240 Head_Flying_Hours       ------   100   253   000    -    9154 (175 176 0)
241 Total_LBAs_Written      ------   100   253   000    -    3303158006
242 Total_LBAs_Read         ------   100   253   000    -    311058680
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01       GPL,SL  R/O      1  Summary SMART error log
0x02       GPL,SL  R/O      5  Comprehensive SMART error log
0x03       GPL,SL  R/O      5  Ext. Comprehensive SMART error log
0x06       GPL,SL  R/O      1  SMART self-test log
0x07       GPL,SL  R/O      1  Extended self-test log
0x09       GPL,SL  R/W      1  Selective self-test log
0x10       GPL,SL  R/O      1  NCQ Command Error log
0x11       GPL,SL  R/O      1  SATA Phy Event Counters
0x21       GPL,SL  R/O      1  Write stream error log
0x22       GPL,SL  R/O      1  Read stream error log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa1       GPL,SL  VS      20  Device vendor specific log
0xa2       GPL     VS    2248  Device vendor specific log
0xa8       GPL,SL  VS     129  Device vendor specific log
0xa9       GPL,SL  VS       1  Device vendor specific log
0xb0       GPL     VS    2928  Device vendor specific log
0xbe-0xbf  GPL     VS   65535  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (5 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
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

SCT Status Version:                  3
SCT Version (vendor specific):       522 (0x020a)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    25 Celsius
Power Cycle Min/Max Temperature:     21/25 Celsius
Lifetime    Min/Max Temperature:     11/37 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:     14/55 Celsius
Min/Max Temperature Limit:           10/60 Celsius
Temperature History Size (Index):    128 (0)

Index    Estimated Time   Temperature Celsius
   1    2015-01-15 20:58    26  *******
 ...    ..( 20 skipped).    ..  *******
  22    2015-01-15 21:19    26  *******
  23    2015-01-15 21:20    27  ********
 ...    ..(  5 skipped).    ..  ********
  29    2015-01-15 21:26    27  ********
  30    2015-01-15 21:27    28  *********
 ...    ..( 10 skipped).    ..  *********
  41    2015-01-15 21:38    28  *********
  42    2015-01-15 21:39    27  ********
 ...    ..(  8 skipped).    ..  ********
  51    2015-01-15 21:48    27  ********
  52    2015-01-15 21:49    26  *******
 ...    ..( 41 skipped).    ..  *******
  94    2015-01-15 22:31    26  *******
  95    2015-01-15 22:32     ?  -
  96    2015-01-15 22:33    21  **
  97    2015-01-15 22:34    22  ***
  98    2015-01-15 22:35    22  ***
  99    2015-01-15 22:36    23  ****
 100    2015-01-15 22:37    23  ****
 101    2015-01-15 22:38    24  *****
 102    2015-01-15 22:39    24  *****
 103    2015-01-15 22:40    24  *****
 104    2015-01-15 22:41    25  ******
 ...    ..( 23 skipped).    ..  ******
   0    2015-01-15 23:05    25  ******

SCT Error Recovery Control:
           Read: Disabled
          Write: Disabled

Device Statistics (GP Log 0x04) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x000a  2            1  Device-to-host register FISes sent due to a COMRESET
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS


Type <return> to exit:
```

After that I decided to run the -a option just to see what it did since I have never run smartmontools before. Here are the results of that:

```
C:\Program Files\smartmontools\bin>
C:\Program Files\smartmontools\bin>smartctl -a sda
smartctl 6.3 2014-07-26 r3976 [x86_64-w64-mingw32-win7-sp1] (sf-6.3-1)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3320613AS
Serial Number:    9SZ6TLSF
LU WWN Device Id: 5 000c50 0206031d8
Firmware Version: CC2J
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Jan 15 23:06:19 2015 CST
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
data collection:                (  617) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off supp
ort.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  69) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_
FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -
       82274666
  3 Spin_Up_Time            0x0003   100   097   000    Pre-fail  Always       -
       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -
       1547
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -
       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -
       69962493
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -
       12019
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -
       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -
       560
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -
       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -
       0
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -
       3
189 High_Fly_Writes         0x003a   092   092   000    Old_age   Always       -
       8
190 Airflow_Temperature_Cel 0x0022   075   063   045    Old_age   Always       -
       25 (Min/Max 21/25)
194 Temperature_Celsius     0x0022   025   040   000    Old_age   Always       -
       25 (0 11 0 0 0)
195 Hardware_ECC_Recovered  0x001a   057   041   000    Old_age   Always       -
       82274666
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -
       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -
       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -
       1
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -
       9154 (206 216 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -
       3303161815
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -
       311061014

SMART Error Log Version: 1
No Errors Logged

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


C:\Program Files\smartmontools\bin>
```

I haven't had a chance to look through it thoroughly yet. I'll do that after I post. I'd appreciate any thoughts. Thanks.

As I look at the SMART report I don't really see anything all that bad. Also, even if the hard drive were bad, that still doesn't explain the bad behavior of both the LiveCD and the LiveUSB while I'm using the desktop machine in question. Right now I'm running the LiveCD on my laptop (that's what I'm using to type this message). It's been working flawlessly for severeal hours using the same LiveCD that won't last 15 min on the desktop machine. So even if the HD is bad, there's got to be more to it. The freezing still occurs even when the HD is totally disconnected fromt he desktop machine.

---

### Post by Yellow Pasque on 2015-01-16
Your SMART data looks odd to me (Why are so many values = 100?). Anyway, if there really are current pending sectors to reallocate, then that's bad. I don't really trust that data though..

> The freezing still occurs even when the HD is totally disconnected from the desktop machine
Ah, I didn't catch that. That's a lot harder to track down if it's not overheating or bad RAM. I would try booting with 'nomodeset' to see if it's an issue with the video card or the open source nouveau driver.
Also, I see some complaints about the fan going bad on MSI GT240. You may want to verify sure yours is still working.

---

### Post by dpilot83 on 2015-01-16
> **Temüjin said:**
> Your SMART data looks odd to me (Why are so many values = 100?). Anyway, if there really are current pending sectors to reallocate, then that's bad. I don't really trust that data though..


Ah, I didn't catch that. That's a lot harder to track down if it's not overheating or bad RAM. I would try booting with 'nomodeset' to see if it's an issue with the video card or the open source nouveau driver.
Also, I see some complaints about the fan going bad on MSI GT240. You may want to verify sure yours is still working.

I don't know enough about the SMART data to know what those values really mean. What does it normally look like? Why is it odd to have a bunch of 100's?

The LiveCD worked much faster when there was no hard drive connected so there was a marked improvement. But it also still freezes regularly as does the LiveUSB.

I just checked the fan on the video card (and all the other fans) and I found them to be working properly.

When I was testing hardware the other day I looked into overheating issues as a possible cause. I can't remember the name of the temperature monitoring tool I installed to monitor temps on the LiveUSB (lm-sensors and psensor?) and then I installed pi and had it calculate pi to 20,000,000 digits. I had to run 6 instances of that simultaneously to get the CPU use to stay maxed out. All the cores on the CPU actually got pretty hot. When it was pegged at 100% usage on each core, their highs ranged from 96C to 99C. However, I never had any problems during the hardest part of the testing. One time it froze shortly after I finished testing. Since psensor was still onscreen I was able to see the exact temperature it froze at and it was something like 47C or so.

I would think if overheating was causing the failures, it would happen when it was really hot. But every time it has frozen and I've had psensor open, the temperature has been below 50C on all the cores and usually below 40C.

I should probably just buy a new hard drive, move my stuff over to it, and run it in Windows and use it. I've killed way too much time on this project but I'd also like to see the fruits of my efforts...

---

### Post by Yellow Pasque on 2015-01-16
Did you try booting with nomodeset? I suspect the nouveau driver could be the cause of the issue. Your GPU isn't exactly "new" to most people, but it takes a while for nouveau devs to reverse engineer support for new GPU's: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

Once Ubuntu 15.04 uses the 3.19 kernel as default, I think you stand a much better chance to be able to run that on Live media, since nouveau is in much better shape for G200 series there.

---

### Post by dpilot83 on 2015-01-16
Not yet. It's past my bedtime so I'll try tomorrow. I did try the nvidia proprietary driver on the LiveUSB yesterday. It worked poorly. As odd as this sounds, every time I typed an "r" in the terminal it would not display at all. "r" would display fine in any other application I tried. There were other weird things as well, but since it didn't seem any better I switched back.

---

### Post by HermanAB on 2015-01-16
I suspect your PSU.  Multiple reasons:
a. The PSU is the least reliable part of a PC
b. PSU problems tend to cause random processing errors and freeze-ups
c. Unplugging the HDD (which draws a lot of power) made it better

---

### Post by dpilot83 on 2015-01-16
> **HermanAB said:**
> I suspect your PSU.  Multiple reasons:
a. The PSU is the least reliable part of a PC
b. PSU problems tend to cause random processing errors and freeze-ups
c. Unplugging the HDD (which draws a lot of power) made it better

Thanks. Is there a way to test the power supply before replacing it? For example, can I hook a digital multimeter to extra power connector and observe power fluctuations under load?

It does seem very odd to me that the computer works fine under Windows, at least after re-installing Windows.

I will say this. When I was installing software on the computer I was trying to conserve bandwidth so I was using a USB drive to transfer software I had already downloaded recently from my laptop to my desktop. I was actually opening the installer directly from the USB drive rather than transferring it to the desktop hard drive. One time the USB lost connection to the desktop while I was installing which resulted in the installer crashing. I thought perhaps I had bumped my knee against the USB drive since the desktop tower sits close to my legs at the desk. However, I really thought I had been careful not to do that. I wonder if power fluctuations could result in unreliable USB connectivity?

Alright, this is embarrassing. I decided to try the LiveUSB on the laptop since I had not done that yet. Before I used it I decided to let it check itself. It came up with 1 error. That didn't really surprise me because of all the times I had to force it to re-boot. I just figured something had gotten corrupted in that process. To be sure though, I booted from the LiveCD and ran the self check on it as well. 1 error there too.

I am very confident I ran that check earlier and it said there were no errors. But maybe I just glossed over the error and didn't read it correctly or something. Anyway, I checked the hashes on the iso and they are correct so I'm burning another copy at the slowest speed my DVD burner will burn it. I'll try again with the new copy and see how it works. I'm going to feel really bad about all the people who have read through this if it was something totally unrelated to the desktop hardware or Linux disagreeing with my hardware somehow. If that turns out to be the case I'll edit the original post at the top so people don't waste their time reading anymore.

Well, the new disc shows one error as well when I do the check with my laptop. However, when I do the check with the desktop it says no errors found. When I do the check on the original disc with the desktop it also says no errors found.

I am creating these discs using the laptop. I find it strange that when I run the self test on both of them with the laptop it finds an error but when I run the self test on both of them with the desktop it finds no errors.

Any ideas?

The laptop is a Lenovo T430 with an i5 professor of some sort and integrated Intel graphics, 16GB of RAM, a 500GB mSATA drive and a 500GB 7200RPM internal drive.

Another piece of the puzzle. When I burned the discs, I was using imgBurn on the Laptop (Windows 7 machine). imgBurn has a verify disc option which I always select. On both discs it said the verification was successful.

I'm currently burning a Mint CD to see how it does.

I'm not even sure where I'm going at this point. There are so many odd things about the whole deal. The desktop has been buggy from day 1 (I regret not building it myself). I remember a BSOD as I was originally installing Windows on it in 2010 or very shortly thereafter. However, this time around it has had a flawless Windows installation. It's just odd to me that it's been buggy for years and now Linux is buggy on it but Windows isn't.

I ordered a new hard drive and I think once that gets here I'm just going to run it in Windows as long as I can. Perhaps I will evaluate the power supply as well. Or perhaps someon has better ideas. I know I'm tired of spinning my wheels. Thanks for the help again everyone.

Alright, so I booted from the Mint CD and it came up with an Ubuntu screen. Turns out that even though I was selecting to boot from the CD drive on the Lenovo T430 laptop, it boots from the USB drive anyway if there is a bootable USB present? I shut down and removed the USB and booted to the CD again. Then Mint came up. So the CD's were probably all good. I just thought I was booting into an Ubuntu CD when I was actually booting into the Ubuntu LiveUSB.

I just tried it again with the USB in and verified I had selected the CD drive as the boot choice and it booted to the USB instead of the CD. Very odd.

I just checked the first of the two Ubuntu discs with the laptop and it checked out fine. At least one mystery is resolved.

---

### Post by dpilot83 on 2015-01-16
Well, it looks like my series of posts was edited into one post by an admin. I'm sure there was a reason but to me it makes it look very difficult to follow what I experienced.

Regardless, it appears the LiveCD is working fine on the desktop now that the messed up LiveUSB is out of the picture and the hard drive is disconnected from the machine. I suspect once the new hard drive comes I'll be able to install a perfectly adequate set of operating systems and software to accomplish the tasks I need to accomplish. Thanks very much to those who helped me in this thread. I really appreciate it.

---

