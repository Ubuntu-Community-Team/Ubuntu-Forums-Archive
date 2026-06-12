---
title: "this location could not be displayed"
date: 2023-10-22
forum: General Help
---

### Post by Unguidedone on 2023-10-22
hello I have this message:

[IMG]https://i.imgur.com/obFOOqa.png[/IMG]

i cant access the entire folder i think the drive might be failing as its might be a hardware issue.

I also had 2 input output errors while copying other files.

heres another:

[IMG]https://i.imgur.com/x9SprMU.png[/IMG]


the drive does use LUKS

[https://manned.org/e2fsck](https://manned.org/e2fsck)

if its a bad block why is it not detected with self tests?

---

### Post by TheFu on 2023-10-25
That's a huge number of read errors. These are the things I watch:
```
smart.2023-10-24.sdb:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
smart.2023-10-24.sdb:  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
smart.2023-10-24.sdb:  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sdb:  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       91377
smart.2023-10-24.sdb:196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sdb:199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sdb:200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
```

See how the last column is all zeros for a disk that's been powered for 91377 hours?  That's over 10 yrs if you do the math.  The three columns in the middle are useless. 

Here's another, younger, HDD:
```
smart.2023-10-24.sdc:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2023-10-24.sdc:  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
smart.2023-10-24.sdc:  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
smart.2023-10-24.sdc:  9 Power_On_Hours          0x0012   088   088   000    Old_age   Always       -       84510
smart.2023-10-24.sdc:196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
smart.2023-10-24.sdc:199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       95

```
Those CRC errors ... means it needs a new cable, usually.
And another ... 
```
smart.2023-10-24.sdd:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2023-10-24.sdd:  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
smart.2023-10-24.sdd:  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
smart.2023-10-24.sdd:  9 Power_On_Hours          0x0012   097   097   000    Old_age   Always       -       27828
smart.2023-10-24.sdd:196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
smart.2023-10-24.sdd:199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

```
and another

```
smart.2023-10-24.sde:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
smart.2023-10-24.sde:  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
smart.2023-10-24.sde:  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sde:  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       91376
smart.2023-10-24.sde:196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sde:199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
smart.2023-10-24.sde:200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```

Do you see a pattern?  All zeros, except the power on hours.

Here's a drive that is really, really, old, almost 12 yrs.  I stopped using it a few months ago, but haven't pulled it from the array.
```
smart.2023-10-23.sdf:  1 Raw_Read_Error_Rate     0x000f   112   089   006    Pre-fail  Always       -       125035716
smart.2023-10-23.sdf:  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
smart.2023-10-23.sdf:  7 Seek_Error_Rate         0x000f   090   060   030    Pre-fail  Always       -       949717079
smart.2023-10-23.sdf:  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       104069
smart.2023-10-23.sdf:199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
smart.2023-10-23.sdf:200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0

```

Weekly, I run short SMART tests.
Monthly, I run long SMART tests.  The results are stored in text files, since for SMART data, a point-in-time doesn't tell the whole story. We need too look over a few months of data to see the rate of change for the values to know if if these parameter values are emergencies or just drives getting older and slowing losing blocks. Hint: massive new errors, all at once isn't good.

---

