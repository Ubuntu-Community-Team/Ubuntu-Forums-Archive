---
title: "Display goes blank after grub!"
date: 2013-06-19
forum: General Help
---

### Post by sahilh14 on 2013-06-19
Hi,

[I]Ubuntu : 11.10 64-bit
[/I]I have ubuntu in dual boot with win 8. The following problem is intermittent.

After selecting ubuntu in the grub screen, a purple screen comes and after 2-3 seconds the display goes blank (where it should prompt for password).
So (after it happened 2-3 times), I just entered my password and surprisingly ubuntu music sounded and I was booted into it **but the display was still showing nothing**.

I don't know whether this is a problem with dual booting or with ubuntu itself. There is no problem when I boot into win 8.
Note : **Sometimes the display works just fine (as I said earlier the problem is intermittent)**.  It's pretty irritating.

Thanx
-Sahil

---

### Post by VMC on 2013-06-19
If it boots at all, then grub is ok. Have you checked log files? ***~home/.xsession-errors***, also ***/var/log/Xorg.0.log***. Mabe even ***dmesg*** output

---

### Post by sahilh14 on 2013-06-20
> **VMC said:**
> If it boots at all, then grub is ok. Have you checked log files? ***~home/.xsession-errors***, also ***/var/log/Xorg.0.log***. Mabe even ***dmesg*** output

Thanks for the reply :)
I'll check the log files later as I don't have that system right now....

But one thing that I don't undersatand is "**why is this problem intermittent?"**
[B]Either it should happen all the time or not happen at all.
[/B][I]
Please Clarify on this if you have any ideas.
[/I]Thanks

---

### Post by VMC on 2013-06-20
> **sahilh14 said:**
> Thanks for the reply :)
I'll check the log files later as I don't have that system right now....

But one thing that I don't undersatand is "**why is this problem intermittent?"**
[B]Either it should happen all the time or not happen at all.
[/B][I]
Please Clarify on this if you have any ideas.
[/I]Thanks
I just noticed you have windows 8. That means UEFI. There instructions on booting Windows 8 with Ubuntu on this forum. 
Can you download boot-info-script (see my blue link below), run it using root, then copy&paste the RESULTS.txt file back here.

---

### Post by sahilh14 on 2013-06-21
> **VMC said:**
> I just noticed you have windows 8. That means UEFI. There instructions on booting Windows 8 with Ubuntu on this forum. 
Can you download boot-info-script (see my blue link below), run it using root, then copy&paste the RESULTS.txt file back here.

Thanks for the reply :)

It seems that the display is gone permanently now. Yesterday, I tried to boot ubuntu 3-4 times but the display showed nothing every time. So running your script is out of picture. :icon_frown::icon_frown:
I'll try it today also and if it doesn't work I'll replace it with 12.04 or 12.10.
I'll keep u posted. :)

Thanks a lot!!

---

