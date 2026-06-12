---
title: "Flashing the bios on a Dell mini 1012"
date: 2015-01-09
forum: General Help
---

### Post by benpietras on 2015-01-09
DON'T DO THIS UNLESS THE RISK OF BRICKING DOESN'T SCARE YOU.

I went from bios version A04 to A12. Had 14.04 installed only.

1) make a freedos bootable stick (I used dd, bs=1M)

2) download the latest bios driver 

[http://www.dell.com/support/home/us/en/19/product-support/product/inspiron-mini1012/drivers](http://www.dell.com/support/home/us/en/19/product-support/product/inspiron-mini1012/drivers)

(I took [COLOR=#444444][FONT=Trebuchet MS]R300869.exe)

3) "sudo apt-get install wine" and then run "wine R300869.exe"

4) cd ~/[/FONT][/COLOR].wine/drive_c/dell/drivers/R300869

There were these files created[COLOR=#444444][FONT=Trebuchet MS]
[/FONT][/COLOR]SAMOSA12.EXE  samosa12.rom  samosrel.txt  Version.txt  WIN_SAMOSA12.EXE

5) copy the R300869 directory to the root of your fdos stick

6) boot the pc from the usb. write "fdos", enter. Select option 4, no drivers.

7) dir (=ls) to see fdos disc file contents. cd to R300869 directory. type "SAMOSA12.EXE"

It flashed for a few minutes, till I accidentally lost contact with the power. Upon reboot it was A12. 





[COLOR=#444444][FONT=Trebuchet MS]
[/FONT][/COLOR]

---

