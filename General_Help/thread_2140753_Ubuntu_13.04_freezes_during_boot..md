---
title: "Ubuntu 13.04 freezes during boot."
date: 2013-04-30
forum: General Help
---

### Post by NBPX on 2013-04-30
Turned on the notebook once and Ubuntu did not recognize the network. I rebooted the computer and Ubuntu started to freeze at the boot screen.

Not a hardware problem. Windows 7 is ok.


Can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2013-04-30
what is on the screen when it freezes? is this a fresh install? can you post what [FONT=courier new]lspci[/FONT] give you when you run it on the live cd?

---

### Post by QIII on 2013-04-30
Is this really 13.10?

---

### Post by oldos2er on 2013-04-30
Moved to Ubuntu +1

---

### Post by NBPX on 2013-04-30
> **QIII said:**
> Is this really 13.10?

Sorry, I meant 13.04.

> **pqwoerituytrueiwoq said:**
> what is on the screen when it freezes? is this a fresh install? can you post what [FONT=courier new]lspci[/FONT] give you when you run it on the live cd?

Plymouth screen. An upgrade from 12.10.

Many thanks for the help, but the system returned to normal.

---

### Post by NBPX on 2013-04-30
> **oldos2er said:**
> Moved to Ubuntu +1

I made a mistake. The version is 13.04.

---

### Post by QIII on 2013-04-30
*Moved back to **General Help.***

;)

---

### Post by pqwoerituytrueiwoq on 2013-04-30
It is probably the crappy 3.8.0-19 kernel, try booting one of your 3.5.* kernels from 12.10 in your grub menu
then you can install the [mainline kernel](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

### Post by NBPX on 2013-04-30
> **pqwoerituytrueiwoq said:**
> It is probably the crappy 3.8.0-19 kernel, try booting one of your 3.5.* kernels from 12.10 in your grub menu
then you can install the [mainline kernel]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme")


uname -a
Linux MyPC 3.8.0-19-generic #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by AzteCypher on 2013-05-04
I too was having freezing issues with 13.04 using the 3.8 kernel.  I found that when I used the 3.5 kernel my freezing issues went away.  Mind you this was on a desktop.

---

