---
title: "Printer error: stuck 'processing page 4' but 'no active job'"
date: 2014-08-08
forum: General Help
---

### Post by Keunes on 2014-08-08
Hello,

I've installed Ubuntu (14.04) for my mum. Almost everything works, but very often there are printing problems. It seems that whenever a document is too large or when a new print job is given when the previous hasn't finished, the printer stucks:

a) the printer hardware gives status 'Printing...' but nothing comes out (anymore)
b) I press cancel on the printer
c) I cancel the job in Ubuntu
d) I try to print something, but nothing happens. Ubuntu says (literally translated): "job in waiting line"
Only after restarting the computer the next job can be performed, printing works again, until the next error occurs. Restarting the printer has no effect.

Looking around on the interwebs I got some commands that seem to help trouble-shooting. One thing that I don't understand that there apparently is that 'lpstat' and 'lprm' give (seemingly) contradicting output. (I know very little about printing & ubuntu, so please bear with me).

```
lpstat -p
printer HP-Photosmart-2570-series now printing HP-Photosmart-2570-series-0.  enabled since vr 08 aug 2014 16:18:02 CEST
    Processing page 4...
```

```
lpstat -s
system default destination: HP-Photosmart-2570-series
device for HP-Photosmart-2570-series: hp:/usb/Photosmart_2570_series?serial=MY722312F404DY
```

```
lprm
lprm: No active jobs on HP-Photosmart-2570-series.
```

The output from 'hp-info -i' gives under Status History that the printer is 'idle'.

The printer is both connected locally through usb and on our network via the router (by cable), I don't know through which connection data is submitted.

[B]I guess my main question is: is there a way to reset CUPS (or whatever thinks my printer is busy) so that I can sent a new job (without having to restart the computer)?
[/B]
PS. My mum is getting on my nerves with this problem, so I would highly appreciate it if you could help me :cool:

---

