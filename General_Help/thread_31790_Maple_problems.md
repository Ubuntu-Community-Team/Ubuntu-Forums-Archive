---
title: "Maple problems"
date: 2005-05-04
forum: General Help
---

### Post by ohzopants on 2005-05-04
I found out the other day that the student maple package I bought last year also has the Linux version included (I was pretty impressed by this), so I installed it.
Everything went fine but now I can only run the command line version (maple) and not the X version (xmaple).  Trying to run xmaple produces no output whatsoever; no windows, no errors not even a f*cking beep.
I checked maplesoft's website and found nothing there so I fired them off an e-mail and their reply was of no use whatsoever.  Does anyone know how to run xmaple in Ubuntu Hoary?
I'm running Hoary on my Toshiba Satelite 2410 laptop and so far am loving it, except that I have to reboot into windows to use wi-fi, vpn and maple (these are works in progress, I'm still learning).

Thanks in advance,
Graham

---

### Post by bularsson on 2005-05-25
Hi,

I've installed maple 9 on Ubuntu Hoary. The graphical version works just fine (I din't try the command line version). Before I used Mandrake 9.2 with the same result. BTW, I have a laptop Toshiba Satelllte A25 307 (Hoary is in it) and wi-fi (Atheros 5000 something) works thanks to madwifi. Did you try it? 

B.

---

### Post by coalquay404 on 2005-05-26
This is a known problem with Maple on Linux. What you want to do is to launch maple using the Classic Worksheet style. From a command line type

```
xmaple -cw
```

It looks ugly compared to the fancy Java version, but all of the functionality is still there.

---

