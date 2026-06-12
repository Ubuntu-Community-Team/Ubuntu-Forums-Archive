---
title: "ata1 COMRESET failed (errno=-16)"
date: 2015-07-05
forum: General Help
---

### Post by Adi_Zebic on 2015-07-05
Hi all,

I recently installed ubuntu 15.04 on my HP elitebook8470p laptop. Since the beginning I'm facing laptop freeze after random time lapse.
In the beginning error was blk_update_request: I/O error, dev sda, sector 538196200
I searched the internet and have made a bunch of tests on my HD, some of them were to check HD health and activate SMART with graphical tool disk utility.
Here is smartctl output -> [http://pastebin.com/QfNQM9jb](http://pastebin.com/QfNQM9jb)

I also have found that TRIM should be active if it's not... and so i did.

hdparm -I /dev/sda |grep TRIM
       *    Data Set Management TRIM supported (limit 8 blocks)
       *    Deterministic read ZEROs after TRIM

 here is hdparm -I output

[http://pastebin.com/V4Bfz5ue](http://pastebin.com/V4Bfz5ue)

After restart all seemd to work correctly since the system started to freeze again. 
As usual, I'm going to ctrl alt F1 to reboot the computer properly and then I saw another message I never seen before -> ata1 COMRESET failed (errno= -16)

As usual, I started searching what possibly could be the solution... and this time dr.google seems to be silent.
I have found a lot of "-32" messages but none about -16.

Do you guys have an idea about what this error is about and how to solve it?

Thanks a lot.

Adi

---

