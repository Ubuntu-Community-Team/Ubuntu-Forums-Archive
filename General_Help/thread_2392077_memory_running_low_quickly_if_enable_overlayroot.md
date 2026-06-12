---
title: "memory running low quickly if enable overlayroot?"
date: 2018-05-16
forum: General Help
---

### Post by heavenscloud on 2018-05-16
Hi,everyone. Last  few days I'm working on a small embeded project using x86 + ubuntu (current using desktop 16.04LTS). 
My platform is J1900 +4G ram +ssd 30G.
Because the platform don't have a secondary power supply, sudden power fault needs to be considered (I think it is inevitable).
After some google I've found a easy solution: the overlayroot on ubuntu, by this link:

   [https://spin.atomicobject.com/2015/03/10/protecting-ubuntu-root-filesystem/](https://spin.atomicobject.com/2015/03/10/protecting-ubuntu-root-filesystem/)


My app just capture some picture, audio and save to the second sata device (manually mount on   /mnt/sata  rw mode by app) with some basic display using QT
So in [COLOR=#4A4A4A][FONT=Monaco]/etc/overlayroot.conf
[/FONT][/COLOR]      [COLOR=#4A4A4A][FONT=Monaco]overlayroot="tmpfs:swap=1,[/FONT][/COLOR][COLOR=#4A4A4A][FONT=Monaco]recurse=0[/FONT][/COLOR][COLOR=#4A4A4A][FONT=Monaco]"

After enable overlayroot and reboot, when app startup

free -m  result:[/FONT][/COLOR] 
----------total        used        free      shared     buff/cache   available
Mem:           3836         888        1554        191         1393        2444
Swap:          7812           0          7812

After app runing 2 hour

[COLOR=#4A4A4A][FONT=Monaco]free -m  result:[/FONT][/COLOR] 
---------total        used        free      shared     buff/cache   available
Mem:           3836         899        1143        203         1792        2420
Swap:          7812           0          7812

another 1.5 hour later:
[COLOR=#4A4A4A][FONT=Monaco]free -m  result:[/FONT][/COLOR] 
---------total        used        free      shared     buff/cache   available
Mem:           3836         896        961        199  1978            2428
Swap:          7812           0          7812

At this moment, I check the memory usage by top  + M   result about 35% free in total

It seems mem will running out soon.
I'll keep it runing for whole night and see if free will drop to a dangerous level, but I think it will......


So I got a few questoin about this overlayroot  method:

1. Why the swap space is never used?   it should be enabled by   [COLOR=#4A4A4A][FONT=Monaco]overlayroot="tmpfs:swap=1,[/FONT][/COLOR][COLOR=#4A4A4A][FONT=Monaco]recurse=0[/FONT][/COLOR][COLOR=#4A4A4A][FONT=Monaco]"
   But swap keeps "0 used" after about 4 hours run.
[/FONT][/COLOR]


2. I've double checked my app, none will write on / , every write is on /mnt/sata. 
   I'think the buff/cache in "free -m " contains two part of  data:
           A: some write pending on / because of the overlayroot, and will be discard if rebooted
               maybe some system service?
           B: some cached data for file just read or write ..etc...

   Is that correct??

   If so, how can I know exactly size of part A? Because if too much write on "/" will finally use up the memory then OOM or some process will be killed by kernel.

3. Is there any way I could know which service or process is or has write to "/" ? And how much it has wrote?
   I want to delete or stop them if they are not necessary.

4. Is there any way I could predict how long will the device run out of memory and needs reboot?
   May be I could change a larger ram for longer run time or smaller ram to cut the cost of total platform.

---

