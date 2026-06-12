---
title: "Mysterious trouble with my desktop"
date: 2016-04-10
forum: General Help
---

### Post by peyre on 2016-04-10
My main computer is a desktop running Xubuntu 15.10 (upgraded from previous versions).  I'm experiencing intermittent, but frequent, problems with it.  I suspect a hardware problem, but am having trouble pinning it down.  It might be the hard drive, might be the computer itself, or possibly the OS, though I suspect it's not the OS.

It's a dual-core machine I bought from IbexPC around 2009.  It has a SATA SSD (OS) and HDD (for data), and a PATA DVD and Zip drive, and 4GB of RAM.

The first signs of trouble started about a week and a half ago; bootups suddenly became very slow: it would sit at the Xubuntu splash screen for a long time before I could log in.  So I backed up an image of the SSD and reinstalled Xubuntu 15.10, several times, but each time it had the same problem.  I figured maybe 15.10 is a little buggy and I'll deal with it until 16.04 comes out, then wipe and do a fresh install.  That was last weekend.

Now, the past few days, I'm having other trouble.  Sometimes it won't boot at all: the computer says "INSERT BOOT MEDIA" or somesuch.  (I opened it up and reseated the SATA connections to the hard drives, and the motherboard cables.  Then it booted ok, but after a while everything stopped working: Whisker menu wouldn't pull up, launchers wouldn't open; I couldn't even open a terminal window to tell it to **sudo halt**.  Other times the past few days the computer has worked ok except it would freeze up for several seconds from time to time, as if it were timing out on something.

So this is all very puzzling.  I thought the problem was with the OS, then I thought the SSD was starting to fail, but now I'm wondering if the mobo is dying or something.  I don't want to start buying hardware on a "Maybe this'll fix it" basis. Anyone have any suggestions?

---

### Post by mastablasta on 2016-04-11
run a SMART scan on disk. looks like it is failing.

have a look: [http://askubuntu.com/questions/325283/how-do-i-check-the-health-of-a-ssd](http://askubuntu.com/questions/325283/how-do-i-check-the-health-of-a-ssd)

another option (if disk is fine) would be bad sata cable.

---

### Post by Impavidus on 2016-04-11
Sounds like a bad SSD, but it could be something different. You could try and disconnect the SSD and install the OS on the HDD. If your problems are gone, it was a bad SSD (or cable connecting the SSD). If not, something else is the problem.

---

### Post by Azdour on 2016-04-11
> **mastablasta said:**
> run a SMART scan on disk. looks like it is failing.

have a look: [http://askubuntu.com/questions/325283/how-do-i-check-the-health-of-a-ssd](http://askubuntu.com/questions/325283/how-do-i-check-the-health-of-a-ssd)

another option (if disk is fine) would be bad sata cable.

I also think that checking the SMART data on the disk would maybe give you an indication if the SSD is failing.  I'm using Xubuntu 14.04 and if you install disk utilities under the Settings menu will be Disks.  Using this application you should be able to see the SMART data for your SSD.

Also as well as a bad sata cable it could be a bad sata connection. If you have spare sata connectors on your motherboard try them and see if the problem remains.

---

### Post by peyre on 2016-04-11
Thanks folks!  I'll boot from a live DVD tonight and try those things.

Also, come to think of it, I can borrow a drive from work (we have a bunch on the shelf), install Xubuntu on that, and see if replacing the drive does the trick.  That ought to be the real test anyway, and if it works I can just order a replacement SSD online, problem solved.  I'll run the SMART tests first though.

I sure hope it's the drive!  I really don't want to buy a whole new computer right now.

---

### Post by peyre on 2016-04-11
Hmm, well.  I booted twice from DVD and neither time could I see my SSD in the file system.  I shut down and plugged in the borrowed hard drive, started boot and went into the BIOS, but it didn't show the borrowed drive(!)  Remembering what you said Azdour, I shut down and switched my drives from SATA0 & 1 to SATA2 & 3 and it booted up fine--though I think it might have lingered on the splash screen.  At this point I'm not eager to quibble about slow bootup as long as it does boot and works fine otherwise.  Maybe it's just a problem with my SATA0 connector on the motherboard.

So I ran **sudo smartctl -a /dev/sdb** on the drive, and it shows the following, in part.  Does this mean anything particular?

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   000    Pre-fail  Always       -       0
  5 Reallocate_NAND_Blk_Cnt 0x0033   100   100   000    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       8736
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       382
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   000    Old_age   Always       -       0
173 Ave_Block-Erase_Count   0x0032   086   086   000    Old_age   Always       -       430
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       192
180 Unused_Reserve_NAND_Blk 0x0033   000   000   000    Pre-fail  Always       -       1036
183 SATA_Interfac_Downshift 0x0032   100   100   000    Old_age   Always       -       0
184 Error_Correction_Count  0x0032   100   100   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   061   050   000    Old_age   Always       -       39 (Min/Max 13/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       16
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       3016
202 Percent_Lifetime_Used   0x0031   086   086   000    Pre-fail  Offline      -       14
206 Write_Error_Rate        0x000e   100   100   000    Old_age   Always       -       0
210 Success_RAIN_Recov_Cnt  0x0032   100   100   000    Old_age   Always       -       0
246 Total_Host_Sector_Write 0x0032   100   100   000    Old_age   Always       -       14092430723
247 Host_Program_Page_Count 0x0032   100   100   000    Old_age   Always       -       447404727
248 Bckgnd_Program_Page_Cnt 0x0032   100   100   000    Old_age   Always       -       3148883420

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%      8736         -
# 2  Extended offline    Completed without error       00%      8736         -
# 3  Short offline       Completed without error       00%      8736         -
# 4  Conveyance offline  Completed without error       00%      8727         -
# 5  Short offline       Completed without error       00%      8727         -
# 6  Extended offline    Completed without error       00%      8724         -
# 7  Extended offline    Completed without error       00%      8719         -
# 8  Vendor (0xff)       Completed without error       00%      8220         -
# 9  Vendor (0xff)       Completed without error       00%      8145         -
#10  Extended offline    Completed without error       00%      8095         -
#11  Conveyance offline  Completed without error       00%      8095         -
#12  Extended offline    Completed without error       00%      8095         -
#13  Short offline       Completed without error       00%      8095         -
#14  Vendor (0xff)       Completed without error       00%      8050         -
#15  Vendor (0xff)       Completed without error       00%      7864         -
#16  Vendor (0xff)       Completed without error       00%      7567         -
#17  Vendor (0xff)       Completed without error       00%      7552         -
#18  Vendor (0xff)       Completed without error       00%      7399         -
#19  Vendor (0xff)       Completed without error       00%      7319         -
#20  Vendor (0xff)       Completed without error       00%      7299         -
#21  Vendor (0xff)       Completed without error       00%      7247         -

```

---

### Post by mastablasta on 2016-04-12
why THRESH is 000 in all cases?! it should say the threshold value which tells you when the disk has issues.

---

### Post by peyre on 2016-04-12
Yeah, a lot of it doesn't make a lot of sense to me.  If it matters, it's a Crucial drive.

What exactly do Pre_fail and Old_age mean anyway?  My first instinct was to assume Pre_fail means the feature is liable to fail soon, but I've seen that a lot on this and several other drives I've run SMART tools on.  I assume Old_age just means use, wear & tear, but no particular indications of failing right away.

---

### Post by peyre on 2016-04-13
Now it's giving the same trouble again.  It doesn't even try to boot; it just says "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" and sits there with the hard drive lit up solid on the desktop unit.  I tried moving the drives to a couple different slots, but still doing the same thing.  Anyone have any suggestions?  I'm at my wits' end.

---

### Post by mastablasta on 2016-04-14
VALUE -current value at the time of scan 
 WORST - your worst value achieved at any scan (usually i think they get scanned on boot) 
THRESH - value where disk will have issues.

values are often converted into some kind of percentage to be easier to understand and compare than raw value.

some tools offer a deeper scan of the disk. perhaps that would reveal more or provide better data?

---

