---
title: "All printing stops!"
date: 2007-05-19
forum: General Help
---

### Post by gjtoth on 2007-05-19
A rather bizarre occurence.. after working just fine since a clean install of Feisty, suddenly all print jobs go to queue and sit there.

Printers:
[LIST]
[*]Epson RX620 (USB)
[*]HP LaserJet 6MP (Parallel)
[/LIST]

What I've done so far:
[LIST]
[*]Checked all cables
[*]Powered down/up
[*]Rebooted
[*]Reinstalled CUPS & HPLIP then, rebooted
[*]Uninstalled then reinstalled CUPS & HPLIP then, rebooted
[/LIST]

I've got another system running Gutsy and I've connected both printers to it and they both print fine from there which leads me to believe that something is broke on the Feisty system.

Bear in mind, both printers are detected just fine on their assigned ports.  Just nothing comes out of queue to print.

Anyone?

---

### Post by mbradlcu on 2007-05-21
can you tell me what:
```
lpstat -a
```
produces when the printers are connected, and after a job has been submitted please ; )

---

