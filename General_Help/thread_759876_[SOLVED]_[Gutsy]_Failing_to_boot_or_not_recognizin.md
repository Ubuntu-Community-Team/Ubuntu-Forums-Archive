---
title: "[SOLVED] [Gutsy] Failing to boot or not recognizing hdd"
date: 2008-04-19
forum: General Help
---

### Post by snirpyor on 2008-04-19
Since Hardy gave me some troubles I tried installing Gutsy. The first two times it started from the live CD, but failed to recognize the HDD. The list of file systems came up blank, as did *gparted*.

The HDD is formatted as Ext3 from the Hardy installation. Hardy had no troubles in this department.

The next two boot-attempts failed, dropping into* BusyBox*.

Any suggestions on how to get it to work?

**Some information:**
gigabyte MA78GM (AMD 780g chipset)
samsung spinpoint 500 GB HDD
AMD 4850e CPU
2 GB corsair memory

Using Fail-save settings on BIOS with HDD recognition set to IDE, since AHCI results in fatal GRUB error 18. This is by the way a know issue for this specific motherboard.

---

### Post by bodhi.zazen on 2008-04-19
First thing to check is the integrity of the CD. Check the md5sum of the iso and of the CD.

---

### Post by snirpyor on 2008-04-19
Third time lucky and I am in Gutsy again. I did the CD-integrity check in the boot menu (does that suffice?) and also the memory check. Both came out fine.

edit: update, when performing md5sum on the CD, everything comes out 'ok'.

To clarify: still no HDD

---

### Post by bodhi.zazen on 2008-04-19
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by snirpyor on 2008-04-19
thx, found that, see updated posting. Everything ok

Next installed the catalyst drivers, but that made no difference at all.

---

### Post by bodhi.zazen on 2008-04-19
seems quite odd. hardware problem , loose cable ?

What is the output of :

```
sudo fdisk -l
```

---

### Post by snirpyor on 2008-04-19
Ehm "command not found", am I doing it right?

Loose cable seems unlikely, since I can normally install Hardy (both Kubuntu and Gnome). The issues experienced in 8.04 were of a different nature.

---

### Post by bodhi.zazen on 2008-04-19
Ooops, small type

```
sudo fdisk -l
```

needs a sapce between "fdisk" and "-l"

also that is a small "L" and not the number 1.

---

### Post by snirpyor on 2008-04-19
Tried that as well. Does not echo anything. Neither on /cdrom.

I do not really know what i am doing here though. Something like fdisk on windows boot?

Tried the following as well
```
sudo fdisk /dev/hda
```

To no avail: " unable to open /dev/hda "

---

### Post by snirpyor on 2008-04-19
Should I try with another HDD drive? Got an older IDE device (but do not want to loose data from it yet).

---

### Post by bodhi.zazen on 2008-04-19
Depends on how much you feel like de-bugging this.

but yes, ubuntu is not recognizing the drive and it may be difficult to fix.

---

### Post by snirpyor on 2008-04-19
Well, i will certainly make an effort at this. No telling how successful I will be, since I do not have much spare parts (or OS's) around.

Proposed course of action:

1.   bios update (how do i do that?)

if successful: bios issue, no further action
if unsuccessful: 

2.  windows 2000 installation

if successful: Ubuntu issue, try other linux distro's
if unsuccessful: hardware problem; 

3.  try IDE drive

if successful: faulty HDD-drive
if unsuccessful: other hardware related, try different mainboard

does this make sense? I am in CET, so this get kicked off tomorrow.

---

### Post by snirpyor on 2008-04-20
UPDATE:

I tried flashing the bios with q-flash, but it did not seem to recognize the FDD. 

Next up I hooked up my old IDE-drive with windows 2000 installed (seagate barracuda). It starts to boot from the HDD, but fails with a blue screen (system not fully ACPI compliant).

Finally I tried booting from ubuntu live-cd with the IDE attached, to see if that would get recognized for installation. The system however persisted in booting from the HDD, no matter what boot-sequence setting. And failing with the aforementioned blue screen.

Well I guess it is back to Hardy, unless someone has a better idea. That gives me troubles as well, but at least I have the luxury of a HDD.

And ... Got it all working on Kubuntu 8.04.

---

