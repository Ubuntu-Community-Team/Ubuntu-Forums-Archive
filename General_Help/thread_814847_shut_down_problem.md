---
title: "shut down problem"
date: 2008-06-01
forum: General Help
---

### Post by enemy@network on 2008-06-01
I finally  installed Xubuntu on my system as primary OS.Now there is FREEdom from windows.
However what i see,since my first shut down it doesn't shut the cpu completely
so i have to  press the shut down button finally after waiting for long time . 
error it disaplays is "system is halted"
and still cpu's on/off light is on.
I had 80 GB hard disk.I installed xubuntu on entire disk but now i see only 
68GB.please help me out.

---

### Post by bapoumba on 2008-06-01
Please give some details on your hardware (in particular the video card). There are several bugs lying around:
[lpbug]38915[/lpbug] (see at the bottom)
[lpbug]229043[/lpbug]

---

### Post by ibuclaw on 2008-06-01
I don't think that "**System is Halted**" is an error message.
I think that it is the last thing that is printed before shutdown.

What may be the problem is that Linux is having trouble sending messages to your motherboard/ACPI interface.

It could be something as simple as a small change in your BIOS settings that could fix it.

Although, for the moment it should be alright to use this key combo instead to shutdown your PC.
```
Alt + PrintScreen + o
```
That is the letter "o", **not zero**

The above is what we call a "Magic SysRq Key". It is an efficient way to send messages instantly to the kernel in the event of a possible freeze.
[Read here for more info.]("http://ubuntuforums.org/showthread.php?t=617349")

Regards
Iain

---

### Post by enemy@network on 2008-06-01
Even i think that Linux is having trouble sending messages to your motherboard/ACPI interface.

I had following while errors installing the Xubuntu.
[COLOR="DarkGreen"]MP-BIOS bug:8254 timer not connected to IO-APIC
Kernel panic-not syncing:IO-APIC+Timer doesnot work
Boot with apic=debug and send report[/COLOR]
After lot of googling i got solution to type [COLOR="Red"]F6[/COLOR] in boot screen and type
 [COLOR="Red"]linux acpi=off[/COLOR]
It resolved my problem
I successfully installed xubuntu.How will this problem be now be solved.
what type of setting change is to be done and how now for BIOS.

---

