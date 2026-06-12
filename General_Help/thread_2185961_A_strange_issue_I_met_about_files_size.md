---
title: "A strange issue I met about files size"
date: 2013-11-05
forum: General Help
---

### Post by sgm2772 on 2013-11-05
Dear all,

Had anybody encountered the same problem as mine ?

[COLOR=#000000][FONT=Calibri]root@root # **du -sh  /opt/inventory.list**[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]40K     /opt/inventory.list[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]root@root # **cd /opt/inventory.list**[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]root@root #** ls -l**[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]total 36K[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] 16K -rw-r--r-- 1 test staff **26G** Mar 30  2012 file1[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] 16K -rw-r--r-- 1 test staff **13G **Mar 30  2012 file1_modify[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]4.0K -rw-r--r-- 1 test staff  24 Mar 30  2012   test

I used du command to check the size of the directory, the result was 40K, but it contained 26G+13G big files !!!


Any help or clue will be very appreciated.[/FONT][/COLOR]

---

### Post by Impavidus on 2013-11-05
> **sgm2772 said:**
> 
[COLOR=#000000][FONT=Calibri]root@root #** ls -l**[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]total 36K[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] [COLOR=#ff0000]16K[/COLOR] -rw-r--r-- 1 test staff [COLOR=#ff0000]**26G**[/COLOR] Mar 30  2012 file1[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] 16K -rw-r--r-- 1 test staff **13G **Mar 30  2012 file1_modify[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]4.0K -rw-r--r-- 1 test staff  24 Mar 30  2012   test[/FONT][/COLOR]
The output of ls -l looks peculiar. I didn't expect the sizes in the first column, which differ from those in the centre column. However, if you add up the sizes in the first column I see you get to the same amount as reported by du, taking into account the overhead of the directory itself.

---

