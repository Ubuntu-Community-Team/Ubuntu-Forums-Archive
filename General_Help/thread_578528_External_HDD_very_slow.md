---
title: "External HDD very slow"
date: 2007-10-17
forum: General Help
---

### Post by RurouniJ on 2007-10-17
Hello all.

I am running Feisty on a Compaq NX9105 and have an external Western Digital MyBook Hard disk.

I have encrryped the contents of the hard disk (Although I cannot remember the method used, the process is kcryptd).

Although both Laptop and hard disk are rated as USB 2.0 the transfer speeds are very slow (1-2 MB/sec) which is well short of the 30+ I see quoted as USB 2.0 reachable.

Both reading and writing to the hard disk are slow. I thought it might be the encryption but when reading / writing only 6% or so of the CPU us being used.

This only has 512MB Ram and all of that is used, there is plenty of swap space  unused however.

Does anyone have any ideas as to where the bottleneck is and how I can fix it?

Thanks

RJ

---

### Post by SeanTater on 2007-10-17
Try installing sysstat

Then examine what this command gives:

```
iostat -mxd 3
```

Press CTRL-C to stop the continuous readout

What's the percentage all the way to the right (%util)? Also, what do the columns  rMB/s and wMB/s show?

Try this but change sda to whatever the device for your drive is
```
hdparm -tT /dev/sda
```

The cached reads should be ridiculously high, but the buffered ones are what we are looking for. Also, it can take about 30 seconds some times so be patient.

Unfortunately, I'm not sure if this will work on external drives, but it work for internal ones and cd/dvd drives..

---

### Post by RurouniJ on 2007-10-17
Just found out it looks like Ubuntu is only seeing one port as USB 2.0

lspci output.

00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at e8001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at e8004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

---

### Post by SeanTater on 2007-10-17
For your memory, this command may shed light:

```
vmstat -S M
```
and post the results in a 

[ code ] [ /code ] block except without spaces in the [ ] portions

Only one port as USB 2.0 is completely normal. if you unplug it you'll notice it goes back to 1.1. They all start at 1.1 and switch to 2.0 when a 2.0 enabled device is plugged in.

---

### Post by RurouniJ on 2007-10-17
Thanks for the replies Sean:

I did the first test while writing (iostat)  but the hdparm one while the drive was idle.

[QUOTE=SeanTater;3550301]Try installing sysstat

Then examine what this command gives:

```
iostat -mxd 3
```

Press CTRL-C to stop the continuous readout

What's the percentage all the way to the right (%util)? Also, what do the columns  rMB/s and wMB/s show?

```

Device:         rrqm/s   wrqm/s   r/s   w/s    rMB/s    wMB/s avgrq-sz avgqu-sz   await  svctm  %util
hda              22.00    10.67 44.00  3.33     2.26     0.05    99.94     1.17   25.61  10.00  47.33
sda               0.00   703.00  0.33 257.00     0.00     3.74    29.81     0.82    3.19   3.19  82.00
dm-0              0.00     0.00  0.33 960.00     0.00     3.75     8.00     2.19    2.28   0.86  82.80

```

Try this but change sda to whatever the device for your drive is
```
hdparm -tT /dev/sda
```

```

 Timing cached reads:   1096 MB in  2.00 seconds = 547.80 MB/sec
 Timing buffered disk reads:   66 MB in  3.07 seconds =  21.50 MB/sec

```

vmstat output.

idle:

```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0     33     28    120    107    0    0  1427  1306  858 2245 15  9 22 54

```

While writing
```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 2  1     33      6     31    212    0    0  1417  1414  890 2368 15  9 23 54

```

---

### Post by SeanTater on 2007-10-17
Thanks!

It seems like your a little short on memory, but not terribly so.

Sorry I didn't tell you to read or write while doing the iostat and hdparm, but It like you did anyway, which is good.

Unfortunately, I could not tell which drives you were copying to and from, as they are all busy. Is it possible that your other drives are slower than the external one or that one or several of them are full?

```
df -h
``` should tell.

It's interesting that hdparm and iostat do not show the same results. 20 MB/s is healthy, but 4MB/s is much to slow. Perhaps you need to sample a few more seconds on iostat (I find it's inaccurate the first readout).

---

### Post by RurouniJ on 2007-10-19
Apologies for the late reply Sean,

Unfortunately I am not at the computer in question at the moment however I can tell you the following:

/hda is the internal hard-disk which was the source for the files I was copying, it has copied files between partitions on the same HDD blitzingly fast so that isn't a problem I think.

sda is the USB Hard-disk that is running slowly and causing the problem.
dm-0 is a virtual hard-disk I think that is representing the USB (sda) HDD for encryption purposes. This is why sda and dm-0 have the same numbers.

As to the numbers themselves I took the reading after about 20 seconds of monitoring because most monitoring proggies are skewed at the beginning I find ;)

Thanks

RJ

---

