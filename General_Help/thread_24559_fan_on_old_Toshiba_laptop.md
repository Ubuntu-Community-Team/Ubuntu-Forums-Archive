---
title: "fan on old Toshiba laptop"
date: 2005-04-07
forum: General Help
---

### Post by thierry on 2005-04-07
Hi there !

I installed Ubuntu on my 8 years old Toshiba 430CDS (Pentium 120 MHz, 48 RAM, HDD 1,28 GB). It's doing very well, much better than Win 95, with gdm, Xfce4 !, Dillo (fast!), Abiword... The only thing that doesn't work is the fan. I can't use Toshset b'cause no ACPI support, and Toshutils wouldn't install the module even with apt-get build-dep. It seems it doesn't fit on this old machine. Now all I need is a small program with 2 options fan on / fan off.

On the homepage of Toshutils (Jonathan Buzzard) I found this :

The following pseudo code will turn the fan on :

DISABLE INTERRUPTS
WRITE oxBE TO PORT oxE4
READ byte FROM PORT oxE5
CLEAR BIT o OF byte (i.e. leat significant bit)
WRITE oxBE TO PORT oxE4
WRITE byte TO PORT oxE5
ENABLE INTERRUPTS

The following pseudo code will turn the fan off :

DISABLE INTERRUPTS
WRITE oxBE TO PORT oxE4
READ byte FROM PORT oxE5
SET BIT o OF byte
WRITE oxBE TO PORT oxE4
WRITE byte TO PORT oxE5
ENABLE INTERRUPTS

So my question is simple : is there an easy to use interpreter to convert this pseudo code into a usable program ?

---

### Post by az on 2005-04-07
I do not know if this helps, but I am running a Toshiba 460CDX and the fan just goes on by itself every now and then when the temperature goes up.  It is a bios thing.

I use apm and I can suspend to ram properly, too.  Another bios thing.

---

### Post by thierry on 2005-04-08
Ok thanks for your answer. I updated the Bios but I don't think this will make a difference. I'm sorry but I'm listening carefully and looking with a torchlight : it doesn't move although it gets hot to the point of making mistakes  :twisted:  I even used a match to make it turn a bit because sometimes they get blocked after a long time without use.

This is a serious issue. If it was so easy would it make sense for Jonathan Buzzard to break his head on creating a fan program for old Toshiba laptops ?

---

### Post by thierry on 2005-04-08
If you're having this problem download the fan from [here](http://rpmfind.net/linux/rpm2html/search.php?query=fan) ! and just drop it in your /usr/bin folder  8)

---

### Post by az on 2005-04-08
Did windows make your fan go?

---

### Post by thierry on 2005-04-08
The internal fan on Toshiba laptops is designed to cool the machine down when it gets hot. The fan is linked to a thermocouple and will automatically turn on to prevent the laptop over heating.

However on older laptops this is overseen by the BIOS and does not work under a 32bit operating system such as Linux. (Jonathan Buzzard)

I don't know why it works on yours and not on mine, but I know what I observed : after 6 hours of heating up with cooling method set to performance (max CPU speed and max cooling) the fan should have been moving ! Of course now I deleted Windows 95, I only have 2 bootable floppies to run Tsetup (access the Bios settings) in dos and Flashbios (+ one with sbootmgr to boot from CD and reinstall Ubuntu).

As root fan -n turns the fan on, fan -f turns it off. Fan without option gives me the status of the fan (but I can hear it). This is all I needed  :p

One last note : recently the 15 years old computer-controlled sewing machine of my wife suddenly started smoking, with a smell of burned plastic all over the place...

---

