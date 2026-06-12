---
title: "Brother MFC-J475DW On Ubuntu 14.04 Not Printing"
date: 2015-04-09
forum: General Help
---

### Post by Shea_Oleary on 2015-04-09
I'm new to the Ubuntu world. I installed the two files for my Brother MFC-J475DW printer via the brother website. I tried to print and the screen on the printer shows "Receiving Data" for a few seconds and then goes back to the Idle screen and nothing prints out. 

I checked CUPS, and it shows the below:

[TABLE="class: list"]
[TR]
[TH][&#9660; Queue Name &#9660;]("http://localhost:631/printers/?QUERY=&WHICH_JOBS=&FIRST=%7BFIRST%7D&ORDER=dec")[/TH]
[TH]Description[/TH]
[TH]Location[/TH]
[TH]Make and Model[/TH]
[TH]Status[/TH]
[/TR]
[TR]
[TD][Brother-MFC-J475DW]("http://localhost:631/printers/Brother-MFC-J475DW")[/TD]
[TD]Brother MFC-J475DW[/TD]
[TD]frank-s5-1224[/TD]
[TD]Brother MFC-J470DW CUPS[/TD]
[TD]Idle - "Sending data to printer."[/TD]
[/TR]
[/TABLE]


Any ideas?

Thanks for your help:mad:

---

### Post by Shea_Oleary on 2015-04-11
Wanted to bump this message. Having been trying to get the Brother printer working for the last couple of days.

---

### Post by pdc on 2015-04-11
if we find out what drivers were installed please: if you can paste this command into a terminal; then copy the result and paste it back here please ```
dpkg -l | grep Brother
```

_____________

---

### Post by SeijiSensei on 2015-04-12
I don't know what files you installed from the Brother site, but the simplest method to install the correct drivers is to run the "Driver Install Tool" for your device.  Here is the relevant page for the MFC-J475DW:
[http://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=mfcj475dw_us_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us_ot&lang=en&prod=mfcj475dw_us_as&os=128)

---

