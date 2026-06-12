---
title: "Dapper hangs - need hints please"
date: 2007-06-29
forum: General Help
---

### Post by Chas on 2007-06-29
Our nonprofit group recycle/reuses computers for 
other nonprofit charity groups and I am tweaking 
a Sony Vaio PCG-Z505RX to run lean with Ubuntu 
and Xfce ...

I upgrade this unit to Dapper and during boot up
it will hang about 4 out of 5 times at 
"Loading Hardware Drivers"

When I boot with 2.6.15.-28-386 (recovery mode)
the hang is at this message:

nm256: Mapping port 1 from 0x2709a0 - 0x27ec00

I've google around trying to find hints on how I might
tweak this without success.

Can anyone please give me a hint ... possibly some 
configuration files I should be looking at which may 
need tweaking?

---

### Post by GeeZor on 2007-06-29
is Dapper running HAL ?
Maybe perfom an upgrade to feisty? ```
sudo apt-get upgrade
```

---

### Post by Chas on 2007-06-29
Thanks .. would like to stay with Dapper LTS on this old machine.
Here is some info for others who may run into this problem.

I tried this solution:
[http://ubuntuforums.org/showpost.php?p=977788&postcount=9](http://ubuntuforums.org/showpost.php?p=977788&postcount=9)
and got as far as
sudo module-assistant auto-install alsa-source
but then something in the script stalled.
End result: no progress.

Then, I went into here:
sudo nano /etc/modprobe.d/blacklist
and added this line:
blacklist snd-nm256
End result:
System seems to boot fine now but no sound installed.

Now I wonder if I can manually install the snd-nm256 driver
after boot up when I want sound. I understand that sometimes
it will lock and sometimes it won't, but it is better to take that
chance after boot up because most of the time I don't need sound.

---

### Post by FuturePilot on 2007-06-29
> **GeeZor said:**
> is Dapper running HAL ?
Maybe perfom an upgrade to feisty? ```
sudo apt-get upgrade
```

AFAIK it's not possible to go from Dapper to Feisty. You'd have to make a pit stop at Edgy first.

---

### Post by tgalati4 on 2007-06-29
Sounds like an interrupt or I/O Port problem.  Try turning off the parallel port and serial port off in the BIOS, then try loading the sound module:

sudo modprobe  snd-nm256

There are probably switches after the module that are needed like irq=7, but you will have to search the forums for what combination of switches are needed to wake up your hardware.

Welcome to the community.

Aloha

---

