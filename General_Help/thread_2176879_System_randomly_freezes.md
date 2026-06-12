---
title: "System randomly freezes"
date: 2013-09-26
forum: General Help
---

### Post by Pedro_Matias on 2013-09-26
I have a HP Pavilion dm1-4150sp laptop and sometimes freezes for no reason... Sometimes I am just reading a website for example and it freezes.
First I had Ubuntu 13.04 installed and I thought that if I changed to the 12.04 LTS version, the freezes would stop, but no they still here lol.

The system doesn't freezes very often so it's not a huuuuge problem, but if I can get rid of them it would be perfect.

When the system freezes I can't even REISUB it...

---

### Post by whitesmith on 2013-09-26
It's extremely unusual for the Linux kernel to freeze. That  only happened to me once, a long time ago. Try doing ```
uname -a
``` and post the result so we can determine which kernel you have.

---

### Post by Pedro_Matias on 2013-09-26
Here it is

```

pedro@pedro-HP-Pavilion-dm1-Notebook-PC:~$ uname -a
Linux pedro-HP-Pavilion-dm1-Notebook-PC 3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by whitesmith on 2013-09-26
OK. The kernel is up to date. Check out this thread: [http://ubuntuforums.org/showthread.php?t=2065734&highlight=HP+Pavilion+freeze](http://ubuntuforums.org/showthread.php?t=2065734&highlight=HP+Pavilion+freeze) to read about a possible hardware problem with your machine.

---

### Post by Pedro_Matias on 2013-09-26
Trought the link you gave me I found this one [http://askubuntu.com/questions/190058/hp-notebook-pavilion-g6-2101sl-freeze](http://askubuntu.com/questions/190058/hp-notebook-pavilion-g6-2101sl-freeze). 
I found in the HP site that they released a BIOS update on 16-02-2013. I would love to install the update but the only file they give is a .exe and they say it's only compatible with Windows 7 and Windows 8.... Is there any other way to install the BIOS update?

EDIT: Without using Windows of course lol

---

### Post by crazymonkey05 on 2013-09-26
you could use wine to run the exe but i dont know how stable or safe that would be

---

### Post by Pedro_Matias on 2013-09-26
I thought about using wine too, but like you said I don't know how safe it is... But probably is not :/

---

### Post by whitesmith on 2013-09-26
> **Pedro_Matias said:**
> Without using Windows of course lolI can think of a counterintuitive possibility. If you have the original Win disks for the PC, you could reinstall Windows, flash your BIOS (use a UPS!), and then reinstall Ubuntu. I know what I'm recommending is a PITA, but things like this will sometimes be necessary until manufacturers come to the realization that a substantial number of people use Linux. Wish I had more for you.

---

### Post by jimmy-frydkaer on 2013-09-26
> **Pedro_Matias said:**
> I have a HP Pavilion dm1-4150sp laptop and sometimes freezes for no reason... Sometimes I am just reading a website for example and it freezes.
First I had Ubuntu 13.04 installed and I thought that if I changed to the 12.04 LTS version, the freezes would stop, but no they still here lol.

The system doesn't freezes very often so it's not a huuuuge problem, but if I can get rid of them it would be perfect.

When the system freezes I can't even REISUB it...

You do not mention what DE, Desktop Environment, you use, something that would make helping you a lot easier. But here goes:

After some research of the freezing problems there clearly seem to be some kind of regression in Linux-Kernels prior to kernel 3.10.12 - The reason for this suspicion is that over at Debian Forums we have a few users using GNOME 3 / GNOME-Shell who are experiencing the exact same problem in Debian 7.1 (Wheezy), the only thing NOT freezing is the mouse. None of the ordinary "tricks" help and the only way out is a hard reset of the system. 

The research at Debian Forums up until now have resulted in a picture of random freeze in kernels 3.2.x through 3.10.12. A newly found bug in kernel 3.10.13 makes my hard drive sound like a sub-machine-gun in a drive-by-shooting inside a metal teapot. The freezing problem seem to be a problem on systems using GNOME 3.2.x (GNOME Shell, NOT GNOME Classic) on top of kernels prior to 3.10.12 - Using GNOME-Fallback (GNOME Classic) make the freezes stop on kernels 3.2.x onwards. GNOME 3.4.1 with kernel 3.10.12 also fixes the freezing problem.

---

### Post by Pedro_Matias on 2013-09-27
> **jimmy-frydkaer said:**
> You do not mention what DE, Desktop Environment, you use, something that would make helping you a lot easier. But here goes:

After some research of the freezing problems there clearly seem to be some kind of regression in Linux-Kernels prior to kernel 3.10.12 - The reason for this suspicion is that over at Debian Forums we have a few users using GNOME 3 / GNOME-Shell who are experiencing the exact same problem in Debian 7.1 (Wheezy), the only thing NOT freezing is the mouse. None of the ordinary "tricks" help and the only way out is a hard reset of the system. 

The research at Debian Forums up until now have resulted in a picture of random freeze in kernels 3.2.x through 3.10.12. A newly found bug in kernel 3.10.13 makes my hard drive sound like a sub-machine-gun in a drive-by-shooting inside a metal teapot. The freezing problem seem to be a problem on systems using GNOME 3.2.x (GNOME Shell, NOT GNOME Classic) on top of kernels prior to 3.10.12 - Using GNOME-Fallback (GNOME Classic) make the freezes stop on kernels 3.2.x onwards. GNOME 3.4.1 with kernel 3.10.12 also fixes the freezing problem.

My DE is Unity 2D. 

So what's your suggestion? Upgrade my kernel to the 3.10.12 version and change my IDE to GNOME 3.4.1?
Isn't the 3.8 the latest kernel available for Ubuntu 12.04 LTS?

---

### Post by Pedro_Matias on 2013-09-27
jimmy-frydkaer?

I don't know if this is important or not, and I am not a 100% sure about this, but I think the system only freezes when for example I close the laptop and then I reopen it (suspend/resume) and continue doing what I was doing before... Or for example when screen shuts down and I return and make my login again and continue when I was doing.

---

### Post by Pedro_Matias on 2013-09-27
bump

---

