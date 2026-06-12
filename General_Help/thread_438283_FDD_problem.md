---
title: "FDD problem"
date: 2007-05-09
forum: General Help
---

### Post by Noname02 on 2007-05-09
(I'm reposting this query here as it's a little hectic over there in the n00b's section- which is where this really belongs. Still......)

Ok folks- As a Ubuntu n00b, one last go at this before I use my Ubuntu disk as a birdscarer and find something else to load in the box. Been trying for days to get a handle on this but think I'm getting somewhere at last but need some input now. I was going to dump Linux and all it's works..but this has kinda got me fascinated....

I goes like this:

Version: Unbuntu V 5.10
Problem: System appears to not recognise FDD. everything else (appears) to be ok as far as it's gone. No attempt at online access devices yet. (I daren't!)

Tests: dmesg grep fd (in terminal) gives output: [-C] [-N level] [-S bufsize]
Rightclick FDD in browser > Properties gives: Quantum Fireball 3.6 gB (!)

Conclusion: Unbuntu thinks the FDD is the hard drive hence cannot mount it. (!!) Incidentally, the Hard drive does appear where it's supposed to also, as does the CD Rom.
Before anyone asks, yes, the FDD is plugged into the OBFDD controller as usual! oh yes as well- swopped the FDD and cable for another identical one- still the same.

To give it it's due, it does TRY to read the disk in the drive before giving up so it's got that bit right at least....

Question: How to put it right! I did read on the forums about a bug in some Ubuntu versions affecting FDD's. Is this it..or something else entirely?
Yours
A morbidly fascinated failed Ubuntu user..

---

### Post by jimbob on 2007-05-09
Please  post the output of the terminal commands:

1:  fdisk -l
2.  cat /etc/fstab

Why are you using version 5.10?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by stchman on 2007-05-09
> **Noname02 said:**
> (I'm reposting this query here as it's a little hectic over there in the n00b's section- which is where this really belongs. Still......)

Ok folks- As a Ubuntu n00b, one last go at this before I use my Ubuntu disk as a birdscarer and find something else to load in the box. Been trying for days to get a handle on this but think I'm getting somewhere at last but need some input now. I was going to dump Linux and all it's works..but this has kinda got me fascinated....

I goes like this:

Version: Unbuntu V 5.10
Problem: System appears to not recognise FDD. everything else (appears) to be ok as far as it's gone. No attempt at online access devices yet. (I daren't!)

Tests: dmesg grep fd (in terminal) gives output: [-C] [-N level] [-S bufsize]
Rightclick FDD in browser > Properties gives: Quantum Fireball 3.6 gB (!)

Conclusion: Unbuntu thinks the FDD is the hard drive hence cannot mount it. (!!) Incidentally, the Hard drive does appear where it's supposed to also, as does the CD Rom.
Before anyone asks, yes, the FDD is plugged into the OBFDD controller as usual! oh yes as well- swopped the FDD and cable for another identical one- still the same.

To give it it's due, it does TRY to read the disk in the drive before giving up so it's got that bit right at least....

Question: How to put it right! I did read on the forums about a bug in some Ubuntu versions affecting FDD's. Is this it..or something else entirely?
Yours
A morbidly fascinated failed Ubuntu user..

Try a newer version of Ubuntu.  Also, who uses floppies anymore?  I have not used one in sometime.  I have a floppy on a machine and it works, I RARELY use it.  To use a floppy go to the Computer icon and double click on the floppy.  This will mount the floppy.  After you mount the floppy you can browse it with Nautilus.  Just remember to Eject the floppy by right mouse clicking on the icon before you press eject on the drive itself.

So floppy support is the most important thing to you?

---

