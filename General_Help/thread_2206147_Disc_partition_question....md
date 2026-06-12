---
title: "Disc partition question..."
date: 2014-02-17
forum: General Help
---

### Post by bc.haynes on 2014-02-17
I used gparted to wipe and partition my 500 GB external disc to use as a backup disc.

Does the disc take 7.46 GB for "housekeeping. (See screenshot) What is this used for?

[ATTACH=CONFIG]250436[/ATTACH]

---

### Post by david98 on 2014-02-17
The difference in capacities is due to two different methods for defining what exactly the prefixes mega, giga, tera mean. In the computer world, these prefixes have different meanings depending on what exactly you are talking about. Hard drive manufacturers report the size of hard drives using the decimal definition of these terms (10^6, 10^9, 10^12 resepctively), whereas operating systems and other software use the binary definition of these terms (2^20, 2^30, 2^40).


As you can calculate, these values are close, but not exactly the same. 10^6 is 1,000,000, but 2^20 is 1,048,576. Once we get to larger hard drive sizes, the difference really becomes noticeable.


One gigabyte in binary is 1,073,741,824 bytes (2^30), but in decimal it&#8217;s only 1,000,000,000 bytes (10^9), which is a difference of 73,741,824 bytes (~70MB). So, when we're talking about storage size in gigabytes a hard drive's capacity as reported by the OS will be about 7% less than what is advertised by the hard drive manufacturer

---

### Post by mikewhatever on 2014-02-17
I strongly suspect that in this particualr case, the "Used" collomn reports the number of reserved blocks.
Check the output of <sudo tune2fs -l /dev/sdb1 | grep -i block> (-l=- and small L).

---

### Post by oldfred on 2014-02-17
Three things and two discussed above.
The difference of decimal vs binary.
The space that journal for formatted drives.
And reserved space for superuser that Linux uses to prevent crash. If just data you can reduce or eliminate reserved space but you still are responsible if drive gets full.

       Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdb1
see this for more details.
man tune2fs

---

### Post by bc.haynes on 2014-02-17
Thanks** david98 **& **mikewhatever** ,appreciate it.

---

### Post by bc.haynes on 2014-02-17
Thanks, **oldfred** for answering my question. How's thw weather in Chicago?  It's a windy 63 degrees here.

---

### Post by oldfred on 2014-02-17
I am a snowbird. Its 80 where I am. :)

But daughter sent photo of how deep snow is in back yard. :(

---

