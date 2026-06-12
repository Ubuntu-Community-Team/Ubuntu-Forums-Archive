---
title: "HP printer problems"
date: 2017-12-01
forum: General Help
---

### Post by drfox on 2017-12-01
Using Ubuntu 17.10. I have an OfficeJet Pro 6968 running with WiFi and which is automatically detected by linux as HP_OfficeJet_Pro_6960_D6CF0D_  
It's address is "null". And In Settings>Devices>Printers it shows it "Does not accept jobs" I have tried re-adding as a second printer it with its network address, but that fails. I have tried deleting it, but it always reappears. I have tried the 3 or 4 different drivers that I can choose and still it says that it doesn't accept jobs. 
I cannot print to it. 
I have tried adding it in CUPS and get this Printer State message: Idle - File "/usr/lib/cups/filter/foomatic-rip-hplip" not available: No such file or directory
What can I do to get this working?
Thanks

---

### Post by Kirk Schnable on 2017-12-02
Seeing that you have a missing file, do you have hplip installed?

```
sudo apt-get install hplip
```

When it comes to HP web services printers, I've had the best luck running the hp-setup utility from the command line.  It will usually help to configure the printer correctly.  You may need to install the package "hplip-gui" for hp-setup to work.

---

### Post by drfox on 2017-12-02
Thanks, but I do have hplip installed. I attached the printer with an Ethernet cable and it works, but there is still a HP_OfficeJet_Pro_6960_D6CF0D_ printer which is 'not accepting jobs' 
Frustrating.

---

### Post by fyfe54 on 2017-12-02
HP updated hplip to 3.17.11 in the last week or so to support 17.10.  Ut solved my all-in-one printer issues.  Are you using the most recent hplip?

---

