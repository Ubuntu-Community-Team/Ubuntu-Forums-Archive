---
title: "CD-RW not working correctly"
date: 2007-07-14
forum: General Help
---

### Post by nae5 on 2007-07-14
when i put a blank disc in my cd-rw drive to burn an ubuntu.iso i come across some problems.

brasero tells me : There is no disc in "CD-RW CED-8120B":insert a recordable CD or DVD.

right click write to disc says to put in an empty cd-r or cd-rw. 

i tried with cdrecord but im not very good with the command line and could not troubleshoot the errors. (though if someone can help i would not mind this route.)

cdrecord -scanbus sometimes shows my cdrw and sometimes doesn't

root@naestwo:~# cdrecord -scanbus
scsibus0:
        0,0,0     0) 'PIONEER ' 'DVD-ROM DVD-115 ' '1.22' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) 'ATA     ' 'IBM-DTLA-307030 ' 'TX4G' Disk
        1,1,0   101) 'ATA     ' 'WDC WD400LB-55DN' '77.0' Disk
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *
scsibus2:
        2,0,0   200) 'Apple   ' 'iPod            ' '1.62' Removable Disk
        2,1,0   201) *
        2,2,0   202) *
        2,3,0   203) *
        2,4,0   204) *
        2,5,0   205) *
        2,6,0   206) *
        2,7,0   207) *
root@naestwo:~# 
 its not right now..

as well on my laptop the same cd is recognized as blank and i am prompted what to do with it.

so i don't quite understand why is wrong with my cdrw.

if anyone can help it would be greatly appreciated. 

i started this a week or more ago
[http://ubuntuforums.org/showthread.php?t=494363&highlight=cannot+burn+iso](http://ubuntuforums.org/showthread.php?t=494363&highlight=cannot+burn+iso)
and could not make enough sense of the cdrecord howto tutorial that someone linked to get my iso burnt to disc.

thnx for any help given in advance

---

### Post by rfruth on 2007-07-14
hardware problem ?

---

### Post by ReaderRat on 2007-07-14
> **rfruth said:**
> hardware problem ?

If you are dual-booting with Windoze, does the CDR-RW work in Windoze?

---

### Post by nae5 on 2007-07-14
no im not dual booting windows on this machine, the same cd burner worked when i was using 6.06 a while ago..  ??

thnx for your replies.

---

