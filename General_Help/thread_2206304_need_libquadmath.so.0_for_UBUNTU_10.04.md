---
title: "need libquadmath.so.0 for UBUNTU 10.04"
date: 2014-02-18
forum: General Help
---

### Post by dieter-erich on 2014-02-18
The program 'simple' requests libquadmath.so.0, which I cannot find in the repository. As far as I understand it is part of  gcc 4.7.1, which neither is in the repository. Can anybody give me a hint as how to install this library?! UBUNTU 10.04 64 bit. Thanks

---

### Post by sandyd on 2014-02-18
> **dieter-erich said:**
> The program 'simple' requests libquadmath.so.0, which I cannot find in the repository. As far as I understand it is part of  gcc 4.7.1, which neither is in the repository. Can anybody give me a hint as how to install this library?! UBUNTU 10.04 64 bit. Thanks

Support for Ubuntu 10.04 (desktop) ended in 2013
Please upgrade to/reinstall with Ubuntu 12.04 (which as a bonus will provide you with libquadmath)

---

### Post by dieter-erich on 2014-02-19
Well, thanks, that's what I was afraid of!

---

### Post by mc4man on 2014-02-19
You can check out this ppa & see if you can install a newer gcc-* without issue. 
[https://launchpad.net/~ubuntu-toolchain-r/+archive/test](https://launchpad.net/~ubuntu-toolchain-r/+archive/test)
(I'd add the ppa, update your sources, then use something like synaptic to add a newer gcc. Just pay attention to what is is going to do before proceeding .., it should not replace your current gcc package

---

### Post by dieter-erich on 2014-02-28
Hi mc4man,
   this was it! Installed the newer gcc-* and it works! So, ubuntu 10.04 is still not dead!
Thanks for this hint!

---

### Post by monkeybrain20122 on 2014-02-28
> **dieter-erich said:**
>  So, ubuntu 10.04 is still not dead!


it is dead. Just because you manage to turn it into a zombie or vampire doesn't mean it is not dead. :)

---

### Post by dieter-erich on 2014-04-01
Hi, 
    as I wrote, installing gcc-4.8 and gfortran-4.8 from the repository the link points to worked perfectly on one of my PCs but I then tried the same on my laptop and I now get the message:
./simple_prime: /lib/libc.so.6: version `GLIBC_2.14' not found (required by ./simple_prime)
./simple_prime: /lib/libm.so.6: version `GLIBC_2.15' not found (required by ./simple_prime)

anybody has any idea?
/lib/libm.so.6 exists at this location although of different size on the two PCs (?????)

As far as I found out until now GLIBC seems to be the brain of linux and people write that changing it kills the system. But why did I not get this error message on the other PC, and everything worked well? Of course, both run ubuntu 10.04 with all the recent updates (so shouldn't they behave identically???). And what version do I have????
D-E

---

### Post by mc4man on 2014-04-01
likely can't help you out but maybe ck. the versions, ect. of libc.so.6 & libm.so.6 on both machines to see if they are the same.
to check simply 'run' a .so in the terminal, nothing will 'run' but should print out some info inc. version & more..

Ex here: (I only have 14.04 so the below info/path is not relevant to you..
> doug@doug-Lenovo-IdeaPad-Y510P:~$ /lib/x86_64-linux-gnu/libc.so.6
GNU C Library ([COLOR="#0000FF"]Ubuntu EGLIBC 2.19-0ubuntu3) stable release version 2.19[/COLOR], by Roland McGrath et al.
Copyright (C) 2014 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.8.2.
Compiled on a Linux 3.13.6 system on 2014-03-24.
Available extensions:
	crypt add-on version 2.1 by Michael Glad and others
	GNU Libidn by Simon Josefsson
	Native POSIX Threads Library by Ulrich Drepper et al
	BIND-8.2.3-T5B
libc ABIs: UNIQUE IFUNC


---

### Post by dieter-erich on 2014-04-02
Thanks, mc4man, 

with this one (on PC) it runs:

GNU C Library (Ubuntu EGLIBC 2.11.1-0ubuntu7.13) stable release version 2.11.1, by Roland McGrath et al.
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.4.3.
Compiled on a Linux >>3.2.0-37-generic<< system on 2013-10-02.
Available extensions:
    crypt add-on version 2.1 by Michael Glad and others
    GNU Libidn by Simon Josefsson
    Native POSIX Threads Library by Ulrich Drepper et al
    BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.debian.org/Bugs/>.


and with this one (on laptop) it does not:

GNU C Library (Ubuntu EGLIBC 2.11.1-0ubuntu7.13) stable release version 2.11.1, by Roland McGrath et al.
Copyright (C) 2009 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Compiled by GNU CC version 4.4.3.
Compiled on a Linux >>3.2.0-37-generic<< system on 2013-10-02.
Available extensions:
    crypt add-on version 2.1 by Michael Glad and others
    GNU Libidn by Simon Josefsson
    Native POSIX Threads Library by Ulrich Drepper et al
    BIND-8.2.3-T5B
For bug reporting instructions, please see:
<http://www.debian.org/Bugs/>.

They seem identical versions!

I should say that the laptop is 64 bit and the PC 32 bit. This is probably the reason for the two files having different size. But still...

Could it be that I need to restart the machine? I yet did not try this because I am running something that still needs some days to finish...

---

### Post by mc4man on 2014-04-02
Well when you get a chance to restart do so.
Other possibility? - do you have different versions of simple installed on working vs. non-working machines?
(your working install is @ 2.11 for glibc
Or is there some significant diff in path to the 2 .so's in working vs. non-working installs?

---

### Post by dieter-erich on 2014-04-07
I finally restarted! Same error message!
glibc seem identical versions! However, the laptop is 64 bit and the PC 32 bit. This is  probably the reason for the two files having different size. But since simple was compiled on both PCs separately this should not matter or should it?

---

### Post by dieter-erich on 2014-04-07
I am terribly sorry but the problem with GLIBC apparently occurred because I made an error during compilation (wrong path exported)! Nevertheless, it is not quite clear to me why this led to this particular error message! In any case the installation of gcc-4.8 and gfortran-4.8 worked perfectly! Thanks for helping!

---

