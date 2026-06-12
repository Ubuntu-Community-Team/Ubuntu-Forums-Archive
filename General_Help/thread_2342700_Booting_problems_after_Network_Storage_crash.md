---
title: "Booting problems after Network Storage crash"
date: 2016-11-09
forum: General Help
---

### Post by andi12345 on 2016-11-09
Hello,

Ubuntu 14.04 LTS on a vSphere environment

i have the following Problem:
after a massive crash in my network storage the Ubuntu installation was corrupted. I was able to boot from a live cd and the HDD is mounted/mountable, the data is still "there". After running different tools "[COLOR=#333333][FONT=monospace]fsck [/FONT][/COLOR][COLOR=#660033][FONT=monospace]-a[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dev[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sda1[/FONT][/COLOR]" responds with "no bad blocks everything is fine".

when i try to reboot from the HDD. it shows the purple screen for a second.
if i go to "Advanced Options for Ubuntu" --> Ubuntu, with Linux 3.16.0-30-generic (recovery mode) it goes into the loop again with the lines

Loading Linux 3.16.0-30-generic
error: invalid magic number
Loading initial ramdisk

and back to the loop again.

I know this is a terrible error description but i am kinda out of ideas what to do.

Thank you very much.

---

