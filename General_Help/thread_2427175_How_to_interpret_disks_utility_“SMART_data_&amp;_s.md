---
title: "How to interpret disks utility “SMART data &amp; self-tests” results?"
date: 2019-09-18
forum: General Help
---

### Post by orthoducks on 2019-09-18
Is there any comprehensive explanation of what the statistics in the  report mean? I know about the balloons in the report displays, but many of  them raise more questions than they answer.

I'm particularly puzzled by these questions. If you know answers  please respond, even if you can't point me to a complete information  source.
  
[LIST]
[*]What does "n bad sectors" mean? (To me it means that sectors on  the disk have been mapped out of use because reading and/or writing them caused errors. But I'm looking at a report that says "1 bad sector" and  "reallocated sector count 0, reallocation count 0,"  which makes me wonder what "bad sectors" means to the disks tool.) 
[*]What do the columns of data past "Value" mean? They are  Normalized, Threshold, Worst, Type, Updates, Assessment (that one seems  self-explanatory). 
[*]What are the two different operating temperatures reported (in this case "41 degrees C / 106 degrees C")? 
[/LIST]

---

### Post by TheFu on 2019-09-18
There is no standard.  I've found that only the **smartctl** tool provides raw values for SMART data. None of the GUIs seem to.
For example:```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       3210
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       310
177 Wear_Leveling_Count     0x0013   099   099   000    Pre-fail  Always       -       1
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   067   046   000    Old_age   Always       -       33
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       5
```
That's for a 6 month old SSD.  The last column is all I watch.  Any non-zero value for something that seems like a zero is needed is what I watch weekly.    

Every HDD model has slightly different meanings for each of the reported lines, even within the same vendor's disks.  The best guess explanations come from google searches. I vaguely remember finding some explanations at a data recovery website.

A different disk, 3.5 yrs old, with a cable issue:```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       **101**
  3 Spin_Up_Time            0x0007   164   164   024    Pre-fail  Always       -       400 (Average 450)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       88
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   113   113   020    Pre-fail  Offline      -       42
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       30709
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       85
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       1345
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       1345
194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 20/50)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       **148**
```
The drive is looks fine, but a bad cable is the issue and causing it to be a little slower due to error correction.

---

