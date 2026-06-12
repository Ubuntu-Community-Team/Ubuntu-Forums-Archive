---
title: "PC power off and starting problem"
date: 2024-04-20
forum: General Help
---

### Post by satimis on 2024-04-20
Hi all,

In recent 2 days, "power off" didn't work. The name "Ubuntu" remains on screen, keeping on flashing.  I have to manually switch off the wall switch to shut down the PC.

Today starting PC also encounters problem.  I have to start the PC several times.

Recently I haven't made any change on the settings of PC other than installing software for reading .max files.  Please advise where I have t check?

Thanks in advance.

Regards

---

### Post by Bashing-om on 2024-04-20
Well satimis

Not much detail to know what is not going on -
Here is what I would do:
1) Unclean shutdown calls for an fsck to know the file system is intact and in a consistent state;
2) Boot to TTY from grub's boot menu - any errors on screen ?
    run here:
```

journalctl -p 3 -xb #to filter for errors
journalctl -b |grep failed #see what failed while booting up

```
3) From the TTY attempt to start the GUI; What happens ?

[INDENT]these things happen;
but  it's ubuntu - always fixable[/INDENT]

---

### Post by satimis on 2024-04-21
> **Bashing-om said:**
> Well satimis

Not much detail to know what is not going on -
Here is what I would do:
1) Unclean shutdown calls for an fsck to know the file system is intact and in a consistent state;
2) Boot to TTY from grub's boot menu - any errors on screen ?
    run here:
```

journalctl -p 3 -xb #to filter for errors
journalctl -b |grep failed #see what failed while booting up

```
3) From the TTY attempt to start the GUI; What happens ?

[INDENT]these things happen;
but  it's ubuntu - always fixable[/INDENT]
Hi Bashing-om,

Thanks for your advice.

Performed shutdown and start-up tests.  Now I can shutdown and start-up the PC.  Please see attached warnings captured with mobile phone

Regards

---

### Post by yancek on 2024-04-21
An alternative to pulling/turning off a wall switch is the simple method explained at the site from the link below.  What it does, how it works is also explained.

 [https://www.borfast.com/blog/2022/01/16/how-to-safely-restart-a-crashed-linux-system-a.k.a.-reisub-gentle-restart/](https://www.borfast.com/blog/2022/01/16/how-to-safely-restart-a-crashed-linux-system-a.k.a.-reisub-gentle-restart/)

---

### Post by Bashing-om on 2024-04-21
satimis - Ouch

Those errors: Does not look real good for the home team.
1) Power supply failing ?
2) SATA cable gone bad ?
3) Bad SATA connections at either the drive or controller ends ?
4) Failing drive ?

-let the process of elimination begin-

---

### Post by satimis on 2024-04-21
> **Bashing-om said:**
> satimis - Ouch

Those errors: Does not look real good for the home team.
1) Power supply failing ?
2) SATA cable gone bad ?
3) Bad SATA connections at either the drive or controller ends ?
4) Failing drive ?

-let the process of elimination begin-
Hi Bashing-om,

Whether allows the start process to eliminate the errors automatically by themselves.

I couldn't find current(cy) under C

Regards

---

### Post by Bashing-om on 2024-04-22
satimis; Oh boy no

> 
eliminate the errors automatically by themselves.

No auto to this - just hard work.

run those errors through uncle Google's search and it will be readily apparent that this could well be a hardware issue.
- Clean the SATA contacts (spray tech-in-a-can); small bristle brush
then run a file system check from the liveUSB
- Still with errors - replace the SATA cable
then again run a file system check
-still with errors - 
then run a SMART test on the drive:  [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

These are good places to start - depending on results is what is then to be done,

edit: Power supply not loaded down with a bunch of added devices is it ?

[INDENT]no easy button :([/INDENT]

---

### Post by satimis on 2024-04-22
> **Bashing-om said:**
> satimis; Oh boy no


No auto to this - just hard work.

run those errors through uncle Google's search and it will be readily apparent that this could well be a hardware issue.
- Clean the SATA contacts (spray tech-in-a-can); small bristle brush
then run a file system check from the liveUSB
- Still with errors - replace the SATA cable
then again run a file system check
-still with errors - 
then run a SMART test on the drive:  [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

These are good places to start - depending on results is what is then to be done,

edit: Power supply not loaded down with a bunch of added devices is it ?

[INDENT]no easy button :([/INDENT]
Hi@Bashing-om

Performed tests as follows;
1 Change another SATA cable of the OS hard drive but problem still remains
1.1 Start-up with warnings remains
1.2 Shutdown without problem.

2. Change connection of the OS hard drive to another port of the motherboard.  Hard drive couldn't be detected.

I don't know whether it is on account of the OS hard drive - SATA3 2TB SSD ?
OR
The problem comes from the PC ?

This is a dual-boot PC
1. Ubuntu 22.04 - SATA3 2TB SSD
2. Ubunut 22.04 - SATA3 250G SSD
3. Windows 10 - SATA3 500G SSD

There is no problem booting 2. and 3. above

Any advice?  Thanks

Regards

---

### Post by Bashing-om on 2024-04-22
satimis; Well - making progress :D

> 
Hard drive couldn't be detected.


Begs the question that the controller has issues.
so:
Boot 2) and execute terminal command;
```

sudo fdisk -lu

```
Is drive 1) seen ?
no ? then shut down and change the SATA port on the controller - boot back up to 2) and see now if fdisk sees the drive.
else
well, try and see if smartctl on that 1st drive shows good/bad/indifferent.

rebooting often enough to have a clean boot attempt.

The good thing here is as 2 and 3  drives are in good shape, the power supply is also in good shape :D

AND!
Still not confirmed (fsck) that the file system is intact // one could also run the fsck check from the SATA3 250G SSD - one can not run the check while 1) is mounted/in use. However; if fdisk fails to detect the drive fsck will also fail. Does BIOS see the drive ?

[INDENT]bad things can happen
[/INDENT]

---

