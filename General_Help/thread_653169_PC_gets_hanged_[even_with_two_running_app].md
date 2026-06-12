---
title: "PC gets hanged [even with two running app]"
date: 2007-12-29
forum: General Help
---

### Post by joey645 on 2007-12-29
My PC is suddenly experiencing incredibly low performance.

Even if i start two application like Ktorrent & Firefox, problem occurs. First, Firefox gets getting jerky and then hangs.And then the whole PC hangs.

Could any plz tell me any command/scripts to check what is going on in my PC,

Sometime back i had problems with ACPI[PC was getting hanged for few seconds periodically, Cause was found after grepping acpi.., ACPI log was getting written continuously..] So, i keep acpi=off in my boot option.

Plz reply back, if you know how to detect what is happening behing the GUI & where the CPU usage is getting sapped.

Thanks!!

---

### Post by Furat on 2007-12-29
Sometimes PC hanged  because of CPU overheating  , check the temperature of your CPU

---

### Post by p_quarles on 2007-12-29
You can find out what's eating up resources by running this:
```
ps aux |  less
```
Scroll through the output, and look for the processes that have the highest values in the CPU and MEM columns.

---

### Post by joey645 on 2008-01-13
i executed the command 
```
ps aux |  less
```
and got a long output... the first few lines are as below

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2952   280 ?        Ss   00:12   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   00:12   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   00:12   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   00:12   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   00:12   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   00:12   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   00:12   0:00 [khelper]
root        26  0.0  0.0      0     0 ?        S<   00:12   0:00 [kblockd/0]
root        27  0.0  0.0      0     0 ?        S<   00:12   0:00 [kacpid]
root        28  0.0  0.0      0     0 ?        S<   00:12   0:00 [kacpi_notify]
root       107  0.0  0.0      0     0 ?        S<   00:12   0:00 [kseriod]
root       127  0.0  0.0      0     0 ?        S    00:12   0:00 [pdflush]
root       128  0.0  0.0      0     0 ?        D<   00:12   0:00 [kswapd0]
root       179  0.0  0.0      0     0 ?        S<   00:12   0:00 [aio/0]
root      1957  0.0  0.0      0     0 ?        S<   00:12   0:00 [ksuspend_usbd]
root      1958  0.0  0.0      0     0 ?        S<   00:12   0:00 [khubd]
root      2023  0.0  0.0      0     0 ?        S<   00:12   0:00 [ata/0]
root      2024  0.0  0.0      0     0 ?        S<   00:12   0:00 [ata_aux]
root      2099  0.0  0.0      0     0 ?        S<   00:12   0:00 [scsi_eh_0]
root      2100  0.0  0.0      0     0 ?        S<   00:12   0:00 [scsi_eh_1]
root      2314  0.0  0.0      0     0 ?        S<   00:12   0:00 [kjournald]
root      2519  0.0  0.1   3028   264 ?        S<s  00:12   0:00 /sbin/udevd --d
```

My PC was running in jerky condition at the time of executing above.

Could anyone tell how to diagnose what is the problem with my PC.
I am not using any eye candy or any RAM sapping application.

Plz reply if anyone can help!!

---

### Post by joey645 on 2008-01-18
I'm still experiencing the low performance problem. It was not there all the time[Just told to clear doubts on my M/C configuration capable of handling Ubuntu]

Can anyone tell how to check where any service is writing into the logs?

---

### Post by anthonyJC on 2008-01-18
you got SATA or (P)ATA  drive? or if you don't know what is the model number of the branded pc. Compaq Presario doesn't say when it made (ie specs.) if you don't have 512mb ram its gonna page. find a torrent client with a smaller memory footprint (ktorrent requires kdelibs-if your on ubuntu.) bitorrent with curses  interface is good. i read a response in the forums today there is a console based one.

---

