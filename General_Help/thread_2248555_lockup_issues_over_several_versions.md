---
title: "lockup issues over several versions"
date: 2014-10-15
forum: General Help
---

### Post by Quatermain on 2014-10-15
Hello,

Over the last month or so I've been having issues with a machine running ubuntu.  

It does this with every other similar program I've tried, but I have primarily been trying to use the trinity transcriptome assembler.
It builds packages and programs without issue, and I've gotten certain datasets assembled with trinity without a problem.

The symptoms:
-It locks up under load randomly.  
-It is a complete lock up, can not SSH into the machine or get it to restart with any of the key combinations I am aware of.  c+a+d, alt+sys+reisub, ctrl+alt+esc

Things I have tried to fix it:
-I started with an un-updated copy of 12.04, updated it fully
-updated to 14.04
-under both versions, I did ctrl+alt+f1 and sudo stop lightdm before running programs.
-I have run memtest and no errors were found
-cpu temp hasn't gone above 44C for any of the cores
-haven't been able to find anything in syslog or dmesg that looks relevant

I'm looking for a way to monitor CPU voltage as my next idea.

Any help would be greatly appreciated, sys specs are below.


SUPERMICRO MBD-X9DAi-O
(2) E5-2603 Sandy Bridge-EP 1.8GHz 
128 GB ECC memory DDR 1600
Nvidia GT610
SAMSUNG Spinpoint F3 1TB
[FONT=&quot]LSI00202 9260-8I Raid controller (I've taken the raid out of the loop and still have the problem- though it is still plugged into the board, everything is just running on the single samsung drive)[/FONT]

---

