---
title: "[SOLVED] Erroneous &amp;quot;minimum 256 mb ram&amp;quot; error message"
date: 2008-04-11
forum: General Help
---

### Post by EtniesBMX on 2008-04-11
I'm rockin' a Dell c800 laptop with 256 mb ram and a PIII 800mhz. I'm trying to run WUBI on Win XP to install Xubuntu, and I get this error message: "You need at least 256MB memory to run the installer!"

I have exactly 256mb. Is there anything I can do to get Wubi to bypass this error message and allow me to install it on my machine? Any help would be appreciated.

---

### Post by ago on 2008-04-12
please attach the wubi log in your user temp folder (%temp%)

---

### Post by kerry_s on 2008-04-12
> **EtniesBMX said:**
> I'm rockin' a Dell c800 laptop with 256 mb ram and a PIII 800mhz. I'm trying to run WUBI on Win XP to install Xubuntu, and I get this error message: "You need at least 256MB memory to run the installer!"

I have exactly 256mb. Is there anything I can do to get Wubi to bypass this error message and allow me to install it on my machine? Any help would be appreciated.

you may have 256mb installed, but the system takes some.
for instance i have 256mb installed, but only 251mb can be used by me/the system.

---

### Post by ago on 2008-04-12
Yes the log will confirm that, but the actually memory seen might be less than the one installed. In any case I have had mixed report from people who had exactly 256MB in the past, so I am quite in favor of having a slightly stricter limit. I will later produce a version that will (optionally) skip the check (please remind me after final)

---

### Post by EtniesBMX on 2008-04-12
> **ago said:**
> please attach the wubi log in your user temp folder (%temp%)

Here you go. Looks like it's seeing 255mb RAM. Ah, so close!

---

### Post by ago on 2008-04-12
[http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev485sh.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev485sh.exe)

run it with "--skipmemorycheck"

---

### Post by EtniesBMX on 2008-04-12
> **ago said:**
> [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev485sh.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev485sh.exe)

run it with "--skipmemorycheck"

You are the man. Thanks!!

---

### Post by Montoyaminor on 2008-04-12
I have the same problem, but im sort of a noob so i dont even know how to run with "--skipmemorycheck" :mrgreen: could you explain please?

---

### Post by EtniesBMX on 2008-04-12
> **Montoyaminor said:**
> I have the same problem, but im sort of a noob so i dont even know how to run with "--skipmemorycheck" :mrgreen: could you explain please?

no problem...open a command prompt in windows (Start>Programs>Accesories>Command Prompt). Navigate to the folder  with the Wubi-8.04-beta-rev485sh.exe file (using "cd" to change directory and "dir" to list directory contents), then execute it with the "--skipmemorycheck" option

```
 Wubi-8.04-beta-rev485sh.exe --skipmemorycheck
```

if you need more help just ask

---

### Post by Montoyaminor on 2008-04-12
Thank you very much! i got past the error,and I am on my way to a better OS =D

---

### Post by mentolution on 2008-04-29
I'm having the same issue, machine has 256Mb total but some is being used to run windows. I just started today so I'm next to clueless as well. How do you navigate to the folder with the command prompt? Typing "dir" in the prompt box will make a short directory of C: contents, but "cd" doesn't do anything. Once past thathow do I excute?

---

### Post by ago on 2008-04-29
Try [http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev503.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-beta-rev503.exe)

---

### Post by EtniesBMX on 2008-04-29
> **mentolution said:**
> I'm having the same issue, machine has 256Mb total but some is being used to run windows. I just started today so I'm next to clueless as well. How do you navigate to the folder with the command prompt? Typing "dir" in the prompt box will make a short directory of C: contents, but "cd" doesn't do anything. Once past thathow do I excute?

type cd [foldername] until you navigate to the folder you're trying to get to. for example if you're at c: you can type "cd windows" and you'll enter the windows directory

---

### Post by CamHart on 2008-04-30
the --skipmemorycheck worked wonders <3

---

