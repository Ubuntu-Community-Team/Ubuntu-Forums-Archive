---
title: "Ubuntu won't start after installing sound driver"
date: 2008-06-01
forum: General Help
---

### Post by avrilrox on 2008-06-01
Ok, so i am using the onboard sound card on my ASUS P5L-MX motherboard.

**What happened?**
The sound was low quality under Ubuntu but it was fine under Windows so i decided to install the drivers for **linux.**

I got my drivers here:
[http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5L-MX](http://support.asus.com/download/download.aspx?SLanguage=en-us&model=P5L-MX) (click on Others)
This is the direct link:
[http://dlsvr03.asus.com/pub/ASUS/mb/socket775/P5L-MX/LinuxDrivers.zip](http://dlsvr03.asus.com/pub/ASUS/mb/socket775/P5L-MX/LinuxDrivers.zip)

I installed them and everything was fine until i rebooted.
It goes to the login screen so i write my username and password and then it says that there was a missing file and logs me out.


What should i do?


Thanks.

---

### Post by quelx on 2008-06-01
Exactly what error does it give?

---

### Post by xfceuser on 2008-06-01
try to boot in the recovery mode ...

---

### Post by Victormd on 2008-06-01
Not sure I understand your problem... it logs you out to the login screen? And does it cycle (i.e., same behavior all the time)? Does it say what file is missing? If so, you can try to create/replace/copy the file using CTRL+ALT+F2. Or, you can CTRL+ALT+F2 and remove the driver, reboot and see if you can login...
Can you post the error that you're getting?

---

### Post by SirPerigrin on 2008-06-01
Untill you post the error we can't tell you exactly whats wrong, but the symptoms all point to x being broken. Hardy introduced a new feature in the recovery console to automatically repair x for you. It may be worth a try.

---

### Post by avrilrox on 2008-06-01
> **SirPerigrin said:**
> Untill you post the error we can't tell you exactly whats wrong, but the symptoms all point to x being broken. Hardy introduced a new feature in the recovery console to automatically repair x for you. It may be worth a try.

I tried that and it deleted my graphics driver (low res and looked ugly) but it didnt fix the problem.

It said my session had lasted less than 10 seconds and it asked me if i wanted to see the logs. It said a file was missing.

I used the console to install the program like 2387 times using root but it didnt seem to help.

I reinstalled Ubuntu :/

I am now using a clean installation but the sound doesnt sound very nice and i do not know what to do. If i install these drivers again i might have the same problem.

What should i do?

Thank you very much,

---

### Post by avrilrox on 2008-06-01
Can i set a restore point or something?

---

### Post by SirPerigrin on 2008-06-01
Unless you give us the name of the missing file and the original error message we really can't help you find out what went wrong.

---

### Post by avrilrox on 2008-06-01
> **SirPerigrin said:**
> Unless you give us the name of the missing file and the original error message we really can't help you find out what went wrong.

I see.

Can i create a copy of my settings so that i can restore them if something goes wrong?

---

### Post by SirPerigrin on 2008-06-01
you can backup any files you think may get modified such as
 /etc/X11/xorg.conf by simply saving a copy with a .backup added to the name. These are easily restored later from a terminal.

---

### Post by Victormd on 2008-06-02
> **avrilrox said:**
> I reinstalled Ubuntu :/

I am now using a clean installation but the sound doesnt sound very nice and i do not know what to do. If i install these drivers again i might have the same problem.

What driver are you using now, OSS or ALSA? You can check this under SYSTEM>PREFERENCES>SOUND
If it's all set to autodetect, you might want to try forcing ALSA and see if it improves.

---

### Post by avrilrox on 2008-06-02
> **SirPerigrin said:**
> you can backup any files you think may get modified such as
 /etc/X11/xorg.conf by simply saving a copy with a .backup added to the name. These are easily restored later from a terminal.

In fact, this file can be restored using one of the options given when booting in safe mode but there should be some other file containing the audio drivers. It would be useful to backup that file.

> **Victormd said:**
> What driver are you using now, OSS or ALSA? You can check this under SYSTEM>PREFERENCES>SOUND
If it's all set to autodetect, you might want to try forcing ALSA and see if it improves.

It was set to autodetect.I changed it to ALSA. I'll see if it improves. :)

Thanks everyone!

---

### Post by Victormd on 2008-06-02
Let us know if you notice any difference... :)

---

