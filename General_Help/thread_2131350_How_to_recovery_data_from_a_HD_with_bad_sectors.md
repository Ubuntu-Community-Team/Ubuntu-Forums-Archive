---
title: "How to recovery data from a HD with bad sectors"
date: 2013-04-01
forum: General Help
---

### Post by jumars on 2013-04-01
Hi, 

I'm not a ubuntu user, this is my first time and i need to know how may i get back my data from a hard drive with some errors, I cat access the data through the ubunto explorer but when I saw the properties of the hard drive they said that my 500 gb of data are there but I can´t acces it.

hope that you can help me, and please remember Ubuntu scare me so I have never work with it!!

---

### Post by Bashing-om on 2013-04-01
jumarsl Hi Welcome to the forum.
Whooaaa, back up, slow down, take a deep breath, now give us some information that permits us to help you.

How is the disk in question formated ( NTFS ??)-(Windows) maybe (ext4)-(ubuntu) maybe (htfs)-(Mac)?
Is this drive an internal or external drive ?
What machine is the disk installed in ?
What operating systems and versions are under discussion ?
What methods have you employed to attempt to access the drive ?

Good format to ask a question: simple statement of the situation followed by; I did a and b and c expecting y but the result is X.

Appropriate diagnostic commands may be forthcoming dependent on knowing what commands to provide.
[INDENT=3]
I am try'n to help
[/INDENT]

---

### Post by d0006 on 2013-04-01
I strongly recommend you search "GNU ddrescue", NOT "dd_rescue."  The name is almost the same but GNU ddrescue is better. This has happened to many people and there are many sites that discuss data rescue.  Be prepared to spend some time studying this topic.
Hard disk drive (HDD) failure is pure hell. 
If you are lucky and rescue your data, do WHATEVER it takes to always have a backup. Give up beer, eat ramen for three months, sell your blood, WHATEVER IT TAKES! 

You will be so happy the next time this happens (and it will!) when you can just restore from backup and use the bad drive for refrigerator magnets.

Only follow this link if you want to be even more depressed:
[http://research.google.com/archive/disk_failures.pdf](http://research.google.com/archive/disk_failures.pdf)

---

### Post by jumars on 2013-04-03
> **Bashing-om said:**
> jumarsl Hi Welcome to the forum.
Whooaaa, back up, slow down, take a deep breath, now give us some information that permits us to help you.

How is the disk in question formated ( NTFS ??)-(Windows) maybe (ext4)-(ubuntu) maybe (htfs)-(Mac)?
Is this drive an internal or external drive ?
What machine is the disk installed in ?
What operating systems and versions are under discussion ?
What methods have you employed to attempt to access the drive ?

Good format to ask a question: simple statement of the situation followed by; I did a and b and c expecting y but the result is X.

Appropriate diagnostic commands may be forthcoming dependent on knowing what commands to provide.[INDENT=3]
I am try'n to help
[/INDENT]



Hi 

first thank you for the support. the HD is in NTFS, it is and internal HD but i used with an enclousere for use it throug usd, now it is installed to my desktop that has an ubuntu 12.04. I tried to access the data through the USD and them through the  ubuntu explorer so I connected the HD directly trough a SATA cable.

---

### Post by Bashing-om on 2013-04-03
jumars;

Well, as the disk is formatted "NTFS' that means it is Windows. The best thing to do presently is take that disk to a Window's machine and run Window's diagnostics on it. Window's native tools will be best with Window's file systems. Then one may resort to lower level data recovery if the diagnostics indicate that is needed.
Mark Phelps' advise on recovery of windows files:
[URL="http://ubuntuforums.org/showthread.php?t=2116103"]http://ubuntuforums.org/showthread.php?t=2116103
[/URL][INDENT=2][URL="http://ubuntuforums.org/showthread.php?t=2116103"]
[/URL]hope I have been of some small service
[URL="http://ubuntuforums.org/showthread.php?t=2116103"]
[/URL]
[/INDENT]

---

