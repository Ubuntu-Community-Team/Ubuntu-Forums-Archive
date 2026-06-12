---
title: "hdparm returns very low values for cached reads"
date: 2014-08-13
forum: General Help
---

### Post by Ooki on 2014-08-13
Hey all

My ubuntu 14.04 system is suddenly starting give me sluggish performance (the input would freeze every now and then ect.)
Anyway, looking around in the system I decided to test the hard drive (I had several indications that it might be at fault
e.g. 5 secs between each image when looking though a folder with images using the -> arrow).

Running sudo hdparm -tT gives me some numbers that seems strange so I was wondering what might cause it and/or I
missinterpret these numbers: *note I have done this plenty of times, and all numbers are roughly in the same ballpark*
The fs is ext4 and I have ntfs partition for my dual boot on the same physical drive.

sudo hdparm -tT /dev/sda 
Timing cached reads:     2 MB in  4.50 seconds = 455.17 kB/sec
Timing buffered disk reads:  40 MB in  3.01 seconds =  13.29 MB/sec

(Running it on /dev/sda3 gives the same results)

Now I don't have a SSD drive but looking around on the net seems to suggest that the "cached reads" times are off by a magnitude.
I mean, 2mb in 4.5 seconds?

So, is this normal behavior for a 1 year old HDD, and what can I do to fix this problem?

cheers :)

---

### Post by TheFu on 2014-08-13
Avoid USB.
Have you checked the cables, logs for any related errors?
A failing HDD will often get slower before dying.  Got good, solid, daily, backups?
Could be any of 100 other causes too - PSU, chipset failing, ...

FYI - numbers from my desktop:
```
$ sudo hdparm -tT /dev/vda

/dev/vda:
 Timing cached reads:   14192 MB in  2.00 seconds = 7103.60 MB/sec
 Timing buffered disk reads: 114 MB in  3.12 seconds =  36.53 MB/sec

``` and on a VM server here:
```
$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   17252 MB in  1.99 seconds = 8664.20 MB/sec
 Timing buffered disk reads: 516 MB in  3.01 seconds = 171.39 MB/sec

```
These drives aren't anything special.
On an SSD:
```
$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   5972 MB in  1.99 seconds = 2993.89 MB/sec
 Timing buffered disk reads: 578 MB in  3.01 seconds = 192.29 MB/sec
```

---

### Post by Ooki on 2014-08-13
TheFu - I am not running any USB hard drives at the moment. This is from the built in internal hdd of the system.
I do got a good backup scheme (been burned by that before :D)

But am I correct to interpret that the values im getting is way too low?

Edit:
I see you posted the values, and it sure do like im getting REALLY low speeds.

Any idea where to look next for further diagnostics?

---

