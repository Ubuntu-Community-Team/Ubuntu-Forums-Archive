---
title: "Cannot mount Drive after Electrical Spike"
date: 2015-02-08
forum: General Help
---

### Post by Ifaistos on 2015-02-08
Hello everyone :-)

I have my PC on a UPS because we have cuts in electricity very often lately due to weather.
Just a few minutes ago, there was an cut for a split second, and my PC turned off!!

I really don't know why!  I didn't think that was even possible.

The worst thing though was that I get the error while booting that 
"There was a problem mounting the Drive, press S to skip or M to manually fix"

I am not entirely sure about the wording but it's pretty close.

I tried rebooting a couple of times and it didn't fix it.

I am able to boot but when I try to access the 240GB HD that is mounted under my /home I get this error message :

[B]Error mounting system-managed device /dev/sda2: Command-line `mount "/home/evans/Data240GB"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.[/B]

I am very afraid that my disk is dead.  Nooooooooooooooooo !!!!!!!

I don't have windows on that machine... I am windows clean for some years now.

Could someone please direct me to a resource explaining what I need to do, maybe software to help me diagnose, or anything that could help me find out what happened with the HD.

Is there any hope for the disk to be fine, and need smt really simple?

Maybe someone can help me with the "Manual" procedure of mounting the Disk...

Please help!!

---

### Post by Ifaistos on 2015-02-08
Update :

I read the following :
[http://askubuntu.com/questions/256992/mount-error-after-power-outage](http://askubuntu.com/questions/256992/mount-error-after-power-outage)
[http://askubuntu.com/questions/254581/how-to-save-my-data-in-external-disk/254582#254582](http://askubuntu.com/questions/254581/how-to-save-my-data-in-external-disk/254582#254582)
[http://askubuntu.com/questions/213819/how-to-mount-hard-drive?rq=1](http://askubuntu.com/questions/213819/how-to-mount-hard-drive?rq=1)

I tried to run ntfsck but it couldn't "see" the volume.
I then run ntfsfix, and it worked !  It fixed some flags and now I have access to my volume.

I downloaded the testdisk program but didn't proceed into running it, because it didn't detect correctly the capacity of the volume.

Then I run sudo ntfsck /dev/sda2

This is what I got :

$ sudo ntfsck /dev/sda2

Unsupported: replay_log()
Volume is dirty.
Unsupported: check_volume()
Checking 63676 MFT records.
Unsupported cases found.

Could someone please tell me a way that I could check the integrity of my drive using linux tools?
As I told you I am "windows clean" for quite some time now..

*** While I was writing this message the first time, we have another spike of electricity and my PC turned off again !!!  How is this possible?  My UPS is working!!  When I unplugg it, it supports my computer!!  Does anyone know WHY this is happenning?  It has never happened before !!  Is there something that I could do?  The setting for "sensitivity" on the UPS is set to the highest sensitivity !!

---

### Post by sudodus on 2015-02-08
When thunderstorms are predicted in the weather forecast, I turn off my computers, modems and other sensitive electronics and unplug them. Also disconnect the internet, if spikes could enter the computer that way (for example ADSL via the wired telephone grid).

I think UPS helps when the voltage of the power grid falls (goes to zero) but maybe not when it rises (high voltage spikes). Then you need 'surge protection', and it might work in different ways, maybe protect by disconnecting. So if the surge protection is outside the UPS your computer might keep running. But if the spikes are really bad, I think the only protection is to turn off and unplug.

There are very different capacities of the surge protection equipment. Get some background data via the internet, for example from

[https://en.wikipedia.org/wiki/Surge_protector](https://en.wikipedia.org/wiki/Surge_protector)

---

### Post by Bucky Ball on 2015-02-08
This may a stupid thing to ask, but as you say you have been Windows free for some years, I'll ask it. You are trying to fix NTFS filesystem partitions, I presume? If you have all EXT* partitions, ntfsfix is useless. It is for NTFS partitions. ;)

---

### Post by ajgreeny on 2015-02-08
Unless you have a good reason for needing the disk to be ntfs it would also be safer to use ext4 as it is much more resilient if the power drops and it is hard-shutdown without unmounting.

I assume this is an internal disk, not external USB, and if so why bother with ntfs?  If there is no windows on that machine you are not going to need to be able to read it in a windows environment, so stick with a Linux filesystem, ext4.

---

