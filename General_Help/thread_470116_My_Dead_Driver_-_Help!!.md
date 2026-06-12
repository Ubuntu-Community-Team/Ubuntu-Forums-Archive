---
title: "My Dead Driver - Help!!"
date: 2007-06-10
forum: General Help
---

### Post by Miss Mika on 2007-06-10
:KSHey:KS

I'm really new to Linux and still setting up. 

I just got a new ethanet card. And I can't install the driver.
There is a linux driver on the driver disc it came with

at first I got this.

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** No rule to make target `v2.09e'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

Then I sorted the headders but now I'm getting this.

mike@gobshite:~/Linux v2.09e$ sudo make all => generate ipg.ko
make: *** empty variable name. Stop.

It's an ASUS NX1101 Gigabit network adapter. 
Any help would really be appreciated.

Thanks Mika

---

### Post by empthollow on 2007-06-10
does this require that you do a "./configure" before make?
i would also check if there is some sort of built in support or installable via synaptic.  most hardware is supported by linux out of the box.

---

### Post by Miss Mika on 2007-06-10
Thanks
      
There's not config required and I've added auto network detector ifPlug and Ethadetect still the same reply

mike@gobshite:~/Linux v2.09e$ sudo make all  => generate ipg.ko
Password:
make: *** empty variable name. Stop.

---

### Post by Miss Mika on 2007-06-10
OK I'm still stuck and my eye's are starting to burn from staring at my screen.

tryed the configuration approch but It won't let me do that??
I am so lost...


mike@gobshite:~$ sudo make all  => generate ipg.
make: *** empty variable name. Stop.

mike@gobshite:~$ ifconfig eth0 192.168.102.211 netmask 255.255.255.0
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied

Help!

---

### Post by Miss Mika on 2007-06-10
ok ok I'm a total spastic. the ethanet cable wasn't plugged in right!!:roll:!!

I'm so sorry to have taken up any of your time..

sorry  :oops:

---

### Post by hugmenot on 2007-07-03
You didn&#8217;t actually type this at the end of the line?

```
 => generate ipg.
```

EDIT: funny. [http://www.linuxquestions.org/questions/showthread.php?t=534220](http://www.linuxquestions.org/questions/showthread.php?t=534220)
People writing docs making life hard for necomers.

---

