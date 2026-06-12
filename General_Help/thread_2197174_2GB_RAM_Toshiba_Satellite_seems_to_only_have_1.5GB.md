---
title: "2GB RAM Toshiba Satellite seems to only have 1.5GB RAM?"
date: 2014-01-02
forum: General Help
---

### Post by desconocido on 2014-01-02
I could have sworn that when I bought my Toshiba Satellite C50D with 2GB RAM and Windows 8 a little while ago, I tested it under Windows 8 and it said it had 2GB RAM.

Now I have installed Precise Pangolin 12.04.03 (AMD64) and it says I have 1.5GB RAM (and 1.7GB swap space).

Is that anything to do with Unbuntu or is it more likely a sudden hardware RAM problem?

---

### Post by grahammechanical on 2014-01-02
In Ubuntu that swap space should be a partition of the hard disk. But what utility are you using to find out how much RAM you have? Is it System Monitor? I have seen laptops described as having "shared memory " for the graphics adapter. Is this true of your machine? The missing 0.5GB RAM might be set aside for use by the graphics adapter?

Regards.

---

### Post by desconocido on 2014-01-03
@grahammechanical

Thanks. It could be the graphics. I was using System Monitor to look at RAM.

The computer is described as
Toshiba Satellite C50D-A-11Q
CPU: AMD E1-1200 APU @ 1.4 GHz
Radeon HD Graphics

I have found a Linux command that describes RAM in more detail.
dmidecode –type memory

But I have a new problem with the Toshiba - the keyboard does not work on wake-up and now not on restart. I'll let you know more when I have sorted that out.

---

### Post by desconocido on 2014-01-04
Well, I looked inside the case and it has one 2GB ram card.

Also,
sudo dmidecode –t 17
says it has 2GB ram.

I guess it must be using shared RAM for the graphics.

---

### Post by grier-devon on 2014-01-04
Yes it is your shared memory, if using Unity you could also type "Details" in the search and should be able to find it there as well.

---

