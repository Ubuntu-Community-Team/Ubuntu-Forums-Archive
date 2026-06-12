---
title: "GnomeBaker write error"
date: 2006-08-04
forum: General Help
---

### Post by graabein on 2006-08-04
Hi, I try to backup my private documents and photos and some music and burn it to DVD with GnomeBaker but it just aborts every time. What is wrong here? Can anyone take a look please?

```
Executing 'mkisofs -gui -V BAK2006 -A GnomeBaker -p graabein -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -graft-points Documents=/home/graabein/Documents Photos=/home/graabein/Photos Chopin The Piano Works - Ashkenazy=/home/graabein/Shared/Chopin The Piano Works - Ashkenazy Frederic Chopin - Piano Concerti Nos. 1 and 2=/home/graabein/Shared/Frederic Chopin - Piano Concerti Nos. 1 and 2 Jean Sibelius - Tone Poems & Incidental Music=/home/graabein/Shared/Jean Sibelius - Tone Poems & Incidental Music Jean Sibelius - Tone Poems & Incidental Music@APE=/home/graabein/Shared/Jean Sibelius - Tone Poems & Incidental Music@APE Liszt- The Two Piano Concertos; The Piano Sonata - Richter=/home/graabein/Shared/Liszt- The Two Piano Concertos; The Piano Sonata - Richter | builtin_dd of=/dev/hdd obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.

[...]
Using ENLIGHTENED_XUBUNTU_MAC_000.PNG;1 for  /home/graabein/Documents/pictures/2005-3/enlightened_xubuntu_mac-ox-x2.png (enlightened_xubuntu_mac-ox-x.png)
Using PRIVATE_BILDER_138__MODI000.JPG;1 for  /home/graabein/Photos/2004/8/21/Private bilder 138 (Modified (2)).jpg (Private bilder 138 (Modified).jpg)
Using CHOPIN__FREDERIC___THE_PIANO000 for  Chopin The Piano Works - Ashkenazy/Chopin, Frederic - The Piano Works Disc 13 Various (Chopin, Frederic - The Piano Works Disc 11 Piano Sonatas Nos 2 & 3)
Using CHOPIN__FREDERIC___THE_PIANO001 for  Chopin The Piano Works - Ashkenazy/Chopin, Frederic - The Piano Works Disc 11 Piano Sonatas Nos 2 & 3 (Chopin, Frederic - The Piano Works Disc 10 Mazurkas Op. 50, 56, 59, 63, 67, 68,)
Incorrectly encoded string (m†ne.bmp) encountered.
Possibly creating an invalid Joliet extension. Aborting.
:-( write failed: Input/output error

```

---

### Post by OffHand on 2006-08-04
I do not know what gives this error but I have been unlucky using gnomebaker myself too. You might wanna try k3b:

```
sudo aptitude install k3b
```

p.s. I use aptitude because k3b is a kde app. You can also use apt-get ofcourse.

---

### Post by graabein on 2006-08-04
GnomeBaker has never failed me before and I'd rather not install KDE libs just for accomplishing this task. I could always make room on my laptop and burn the DVD using Nero on WinXP from there...

---

### Post by Sweezel on 2006-08-05
Do you have any idea what "m†ne.bmp" is in your error message? You might have a strangely named file it can't handle.

You might first try turning of the Joliet file system. This is in the options shown right after pressing "create data disk".

---

### Post by Ziede on 2006-08-12
I was having the same problem, turning of the Joliet file system worked like a charm for me, thank you!

---

