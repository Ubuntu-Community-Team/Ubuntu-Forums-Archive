---
title: "Wacom tablet not functioning correctly"
date: 2007-08-05
forum: General Help
---

### Post by ffobsession on 2007-08-05
i tried the detection thing and it says
[I]
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056a ProdID=0015 Rev= 4.03
S:  Manufacturer=WACOM
S:  Product=CTE-440-U V4.0-3
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 40mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=wacom
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms[/I]


so im guessing my driver is right? yes? but my congifure wont read...

[I]neelia@Neelia:~$ cd linuxwacom-0.7.8-2
neelia@Neelia:~/linuxwacom-0.7.8-2$ ./configure --enable-wacom
./configure: line 1199: config.log: Permission denied
neelia@Neelia:~/linuxwacom-0.7.8-2$ [/I]


and when i try to use the pen on my tablet, i have to press down on it to move it around, it wont reach the edges of the screen right, not to mention it keeps shifting places.... it worked better BEFORE i tried installing the tablet.

and i tried reading some FAQ's but im so new at linux that i have no clue what they're talking about....

help pleaseeee ><

---

