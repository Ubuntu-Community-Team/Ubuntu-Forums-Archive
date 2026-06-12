---
title: "rename printer"
date: 2008-05-27
forum: General Help
---

### Post by leona on 2008-05-27
Hi there

ya me again, when I installed the drivers for my hp printer (networked)I seem to have made a mistake with its name, its for some reason now called 'n', erm, its it easy to change its name, I can't see that opion in the properties, is it possible to change its name to something more appropriate or do I have to reinstall it?

Thanks.

---

### Post by leona on 2008-05-29
erm ^bump^ anyone? sorry

---

### Post by prshah on 2008-05-30
> **leona said:**
> Hi there
seem to have made a mistake with its name, its for some reason now called 'n', erm, its it easy to change its name,

backup and edit printers.conf file```

sudo cp /etc/cups/printers.conf ~ 
sudo gedit /etc/cups/printers.conf
```

Look for a line
<Printer n> or <DefaultPrinter n> 
and change the "n" to whatever you want. (No spaces or special characters except "_" allowed in the name). Then restart cups

```
sudo /etc/init.d/cupsys restart
```

If something goes wrong, just put back the old file```

sudo rm /etc/cups/printers.conf
sudo cp ~/printers.conf /etc/cups/printers.conf
sudo /etc/init.d/cupsys restart
```

---

### Post by leona on 2008-05-31
Thank you, that worked a trest xx

---

### Post by noynac on 2008-05-31
I renamed my printer by changing <Printer Deskjet_6980_series> to <Printer Deskjet>. After making this change and resetting the printer, it would not print a page properly (it spit out many pages with odd text). I tried rebooting and changing the DeviceURI, but that didn't help either. 

```
<Printer Deskjet_6980_series>
Info HP Deskjet 6980 series
DeviceURI hp:/usb/Deskjet_6980_series?serial=MY76M1R0YX04YX
State Idle
StateTime 1210174825
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
```

---

### Post by prshah on 2008-06-01
> **noynac said:**
> I renamed my printer by changing <Printer Deskjet_6980_series> to <Printer Deskjet>. After making this change and resetting the printer, it would not print a page properly (it spit out many pages with odd text).

Did you remember to restart cups after changing the name? There was no call to change the URI.

Anyway, restore the backup copy, restart cups, and check if everything is OK. If it isn't maybe you should delete and reinstall the printer.

---

### Post by prshah on 2008-06-01
> **leona said:**
> Thank you, that worked a trest xx

OK! Please mark the thread solved; click on "Thread Tools" _near_ the top right hand side of the page, then select "Mark Thread as Solved".

---

### Post by noynac on 2008-06-01
> **prshah said:**
> Did you remember to restart cups after changing the name? There was no call to change the URI.

Anyway, restore the backup copy, restart cups, and check if everything is OK. If it isn't maybe you should delete and reinstall the printer.

I did restart cups and, just to be sure, rebooted the computer. This didn't help.

I restored the backup copy which got things working again. The name thing is not a big one for me, so I'll just leave things as they are. Thanks for the response.

---

### Post by dvo on 2012-05-16
For manually changing the printer name in current Ubuntu (12.04),
in addition to editing the name in /etc/cups/printers.conf
you need to rename the respective .ppd file in /etc/cups/ppd/

Alternatively, you may simply use the GUI. 
Go to System Settings -> Hardware|Printers, 
select the printer, click on its name, and edit it.

You may also point your browser at [http://localhost:631/printers](http://localhost:631/printers)
to configure your printer, but I did not find a 'rename' option there.

---

### Post by chandan_raka on 2012-07-16
Same problem. Basically I need to do lot of renames and doing it manually in the conf file is time conusming as I have to rename the ppd files as well.

Wondering by CUPS does not has rename option in the web gui.

---

### Post by oldos2er on 2012-07-17
Please start a new thread for your question.

---

