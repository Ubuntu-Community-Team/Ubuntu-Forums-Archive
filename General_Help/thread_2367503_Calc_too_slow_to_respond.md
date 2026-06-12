---
title: "Calc too slow to respond"
date: 2017-07-31
forum: General Help
---

### Post by BigBaka on 2017-07-31
Using Ubuntu 16.04 running Libreoffice 5.3.3.2.

When i try to look at a sheet that contains export of quickbooks data saved on a Windows machine using excel, it takes a full minute or more to open the sheet and the screen dulls to a grey display and unable to do anything. The sheet itself has only 360 or so rows on 20 columns. Every time I switch back from another sheet back to the data export sheet the same problem occurs. Copied and pasted the data into another file and still get the problem. It seems a bit strange that it is having memory problems on a relatively small amount of data!

Any ideas how to fix? Regards, BB

---

### Post by Roger_Coutts_Umste on 2017-12-09
I am using Ubuntu 16.04 LTS running LibreOffice Version: 5.1.6.2
Build ID: 1:5.1.6~rc2-0ubuntu1~xenial2
CPU Threads: 2; OS Version: Linux 4.4; UI Render: default; 
Locale: en-CA (en_CA.UTF-8); Calc: group
and for years after a few minutes of use a large spreadsheet would slow down when I tried to scroll, to the point of the screen dimming and freezing up. Changing the memory graphics cache around did not help. I finally noticed that it always happened after an automatic save, so I disabled autosave and it stopped! I can leave it on for hours and it never slows when scrolling.

---

### Post by HermanAB on 2017-12-10
Try gnumeric instead.

---

### Post by BigBaka on 2018-03-26
> **Roger_Coutts_Umste said:**
>  I finally noticed that it always happened after an automatic save, so I disabled autosave and it stopped! I can leave it on for hours and it never slows when scrolling.

Thanks Roger, I just saw this now, very interesting. Seems very strange and some sort of bug. 9 months later I'm still getting the same problem so will give this a try, although a bit concerned that I'll no longer be getting autosaves? For the record I used to be able to view QB exports back in 2009-12, but for some reason now it always freezes.

---

