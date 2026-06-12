---
title: "Need Scanner Help 14.04"
date: 2016-10-10
forum: General Help
---

### Post by aviator1 on 2016-10-10
Hello All:

Just got an HP 8710 and the printer is working fine.

I have downloaded from HP, but get an error when executing run.

Anyone have any suggestions for getting the scanner part to work.

Thanks for any help.

Regards.

More Info:

I have downloaded HLIP 3.16.9.run  It works to the end, then says there is an error.

More Info:

I can see the 2 other printer/scanners on the network. I will be eliminating them once I can get this one working.

More info again:

Here is what I get whe I run hp-check:
```
HP-Officejet-Pro-l7600
----------------------
Type: Unknown
Device URI: socket://192.168.0.38:9100
PPD: /etc/cups/ppd/HP-Officejet-Pro-l7600.ppd
PPD Description: HP Officejet Pro 8000 a809, hpcups 3.14.3
Printer status: printer HP-Officejet-Pro-l7600 is idle.  enabled since Mon 10 Oct 2016 0Waiting for printer to finish.
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend for HP-Devices.
```

---

### Post by mörgæs on 2016-10-11
I don't know this particular HP but in general I would advise you to use the newest of software (that is, at least 16.04.1 or maybe the daily build of 16.10) when dealing with new hardware. 

You could try first in a live boot.

---

### Post by aviator1 on 2016-10-11
Thanks. May give that a try.

Regards.

---

### Post by aviator1 on 2016-10-11
I upgraded to 16.04, but there was no help with the scanner issue. In fact, I now have 2 printer icons in the settings screen.

Any other suggestions. I hope I am not the only person with this type of printer.

Thanks for any help.

Regards

---

### Post by aviator1 on 2016-10-11
I got it working.

I finally found some instructions regarding installation using Terminal instead of the automatic install wizard.

I also disconnected my other devices to make sure the new one was the only one to be seen.

Still have 2 printer icons in the settings window, but I'm not going to worry or mess with that.

Printing and scanning are working fine.


Regards,

---

