---
title: "CUPS stops all AirPrint Jobs"
date: 2014-08-02
forum: General Help
---

### Post by P_THE_AWESOME on 2014-08-02
Using the CUPS web interface, I enabled sharing for my Brother HL-2270DW laser printer. My iPod Touch sees the printer and I know it's driver is configured correctly because is shows the double-sided option. However, whenever I print something, the iPod acts like it printed fine, but a few seconds later a popup dialog says the printer's name and to "Check the printer for errors." When I log into the CUPS interface and look at the "Jobs" tab, it shows the job as "stopped." The printer doesn't even warm up as if about to print. It never receives the job.

Screenshot of the stopped job:

[IMG]http://s27.postimg.org/t175nfw6r/Air_Print_stopped.png[/IMG]

---

### Post by grier-devon on 2014-08-02
Did you check to see if your printer IP address changed since you set it up? My HP printer changes every 90 days so I have to change the print setting to reflect that.

---

### Post by P_THE_AWESOME on 2014-08-03
It is set up with a [FONT=courier new]dnssd[/FONT] address which automatically finds the right IP. I can print fine from Lubuntu. The address is [FONT=courier new]ddnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/address[/FONT]

---

