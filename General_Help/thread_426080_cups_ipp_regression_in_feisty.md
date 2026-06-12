---
title: "cups ipp regression in feisty?"
date: 2007-04-28
forum: General Help
---

### Post by tholy on 2007-04-28
Hi,

I have an HP multifunction 3300 laser printer(/scanner/fax) connected to a desktop running edgy. The printer is not itself network capable (USB), but the desktop is configured as the server. When my laptop was running edgy, I could send a job to the printer over the network without trouble.

I've upgraded the laptop to feisty (of course, for all I know there could have also been a cups package update to edgy on the server...), and now I can't send a job to the printer over the network. I get the following message in KDE's printer system settings when I ask for the IPP report:

/usr/lib/cups/backend/ipp failed

Attached are the results of running printingbuginfo on both machines.

Thanks in advance to anyone who takes the time to look into this!

---

### Post by Till Kamppeter on 2007-05-16
The print queue names on the server and in the client's URI do not match. On the server you use "HP_LaserJet_3300", on the client "HP_LaserJet_3300_3310_3320". To fix, set the URI on the client to

ipp://192.168.1.2:631/printers/HP_LaserJet_3300

either wit a printer setup tool or running

lpadmin -p HomeNetwork -E -v ipp://192.168.1.2:631/printers/HP_LaserJet_3300

on the client.

   Till

---

### Post by tholy on 2007-05-17
Indeed, that fixed my problem. I had tried a couple of variants, but I think I forgot to include the "printers" part. Thanks so much for taking the time to explain and correct a dumb mistake on my part---you are generous with your own time!

---

