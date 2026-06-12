---
title: "GpsDrive won't start"
date: 2005-04-21
forum: General Help
---

### Post by Scoob_E on 2005-04-21
I'm not a newb, but this is making me feel pretty slow... for the life of me, I cannot get gps drive to start - It seems to hang at the splash screen. There is not any abnormal output on the command line, even when I use either the -d -D (verbose debugging options). This is happening with installs via Apt and fron source.

Scoob

---

### Post by msdoctorus on 2006-07-09
This was happening to me aswell and i have to admit im not new to computers or newb to link but for sure not a pro either, any way on my dell c610 with no built in wifi card so im using cisco 350, my gpsdrive hangs at the splash screen as well but as soon as i pull the cisco card out it will pop right up. I hope someone can shed some light on what is happening there but just letting you know what i did 2 get around it.

---

### Post by FeraTech on 2006-12-31
I'm trying it on my laptop and it's hanging on the boot screen for me too.

---

### Post by Heikki Brotkin on 2007-05-08
Hi,

I had the same problem too and this was only thread I found about this issue. I'll post my solution even though it seems to be quite old thread. 

After some debugging I found out that gpsdrive tries to find GPS device plugged in the computer during the startup. After the first successful startup it will start without the plugged device too. During the first start it will create file "/home/<user>/.gpsdrive/gpsdriverc". 

It seems that first startup succeeds also without the device if there is this configuration file with single line containing serial device. For example:
serialdevice = /dev/ttyUSB0

If you already have a device it's of course easier to plug it in the first place ... ;)

Regards,
Heikki

---

### Post by blakesle on 2007-07-25
Thank you! Thank you! Thank you!\\:D/

---

