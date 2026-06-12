---
title: "won't recognize medibuntu.list"
date: 2007-12-23
forum: General Help
---

### Post by FrankC31 on 2007-12-23
I have done something to Medibuntu.list when I was trying to add additional codecs to view and hear a commercial CD.  When I try to run the "Update Manager" I get the error message:

'E:Type 'http://www.medibuntu.org/sources.list.d/gutsy.list' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

I have tried to modify the file but it won't allow me to save any changes to the file!

As you can probably tell I am very new to Linux.

Ubuntu 7.10 'gutsy gibbon'; on hp laptop Pentium 4  3.0 Mhz 

Thanks,

Frank

---

### Post by itsjustarumour on 2007-12-23
I've been getting exactly the same thing for weeks, but haven't had time to investigate yet...

You should be able to modify the file though - are you sure you're opening it as root user?

---

### Post by p_quarles on 2007-12-23
I've never seen this problem myself. My /etc/apt/sources.list.d/medbintu.list reads like so:
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free
```
Is it significantly different on either of your systems?

---

### Post by fragos on 2007-12-24
I've successfuly added the Medibuntu repositories on a number of machines by following the directions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ~LoKe on 2007-12-24
Edit it using gksudo gedit /etc/apt/whateverthepath/is.lst and remove the space in "list".

---

### Post by itsjustarumour on 2008-01-02
> **p_quarles said:**
> I've never seen this problem myself. My /etc/apt/sources.list.d/medbintu.list reads like so:
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
#deb-src http://packages.medibuntu.org/ gutsy free non-free
```
Is it significantly different on either of your systems?

Hi p_quarles,
Thanks for the post, I've checked and my /etc/apt/sources.list.d/medbintu.list reads exactly the same as yours.
Very strange! ...

---

