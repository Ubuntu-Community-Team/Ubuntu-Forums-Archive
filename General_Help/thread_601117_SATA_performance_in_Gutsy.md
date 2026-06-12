---
title: "SATA performance in Gutsy"
date: 2007-11-02
forum: General Help
---

### Post by jakebolewski on 2007-11-02
I have a T61P laptop with a 7200 rpm drive.  The computer's speed seems to be hindered by the hard drive.  I am getting hdparm -t readings of only 44mb/s.  Is this speed normal?  I thought that 7200 sata disks should be getting numbers around 50-60 mb/s.

-Jake

---

### Post by jerrykenny on 2008-01-13
Hi Jake, hers my present readings

/dev/sda:
 Timing cached reads:   2112 MB in  2.00 seconds = 1056.08 MB/sec
 Timing buffered disk reads:  140 MB in  3.01 seconds =  46.46 MB/sec

The latter figure was ~70 with gentoo, so I'm like you just going to invesigate, will keep you posted.

Footnote . . . . . 
Latest manually compiled kernel hasnt made a whit of difference ! also just remembered the higher figure quoted for gentoo was 64bit  . . . . whereas I've reverted to ubuntu 32 bit

Doh

---

### Post by articpenguin on 2008-01-13
Dosent happen to me.

/dev/sda:
 Timing buffered disk reads:  226 MB in  3.00 seconds =  75.25 MB/sec

mines a seagate 7200RPM Sata.

---

### Post by dicecca112 on 2008-01-13
mines okay

>  Timing buffered disk reads:  174 MB in  3.03 seconds =  57.38 MB/sec
 Timing cached reads:   6250 MB in  2.00 seconds = 3132.15 MB/sec

---

### Post by logos34 on 2008-01-13
> **articpenguin said:**
> /dev/sda:
 Timing buffered disk reads:  226 MB in  3.00 seconds =  75.25 MB/sec

mines a seagate 7200RPM Sata.

wow...you're in raptor territory there.  Is that a perpendicular desktop drive?

---

### Post by articpenguin on 2008-01-13
yes its Perpendicular.

its a Seagate Barracuda 7200.10 SATA 3.0Gb/s 160-GB Hard Drive

---

### Post by logos34 on 2008-01-13
> **articpenguin said:**
> yes its Perpendicular.

its a Seagate Barracuda 7200.10 SATA 3.0Gb/s 160-GB Hard Drive

I was seriously thinking about getting one of those a while back, but I couldn't believe the reviews, and then again I heard they run noticeably louder and a bit hotter (maybe the noise factor is exaggerated though)

---

### Post by articpenguin on 2008-01-13
what was wrong with the reviews?

---

### Post by logos34 on 2008-01-13
> **articpenguin said:**
> what was wrong with the reviews?

they either sounded too good to be true or too negative.  I thought: how could increasing areal density by changing the magnetic orientation of the bits on the platter give that much of a jump in performance?    'I'll believe when I see it' was my attitude.   Others said they were noticeably louder (the last time I checked the pdf specs sheet I think it did show a higher dB level--not much though).  Then I read through a lot of customer reviews at newegg, and quite a few people complained about 'chatter' and heat (but none of that necessarily means anything, it depends on how close or soundproofed the computer is, ventilation, etc.)    I think the reason I never got one came down to the fact that it was at the time still relatively new and unproven, and I'm paranoid about sound.  My case is transparent and sits right next to me on a stand, so even with fan control turned all the way down I hear every little peep it makes.  I'm really thinking seriously about a fanless Antec Phantom power supply, and replacing my stock AMD heat sink fan with the quietest aftermarket fan I can find!  

Anyway, in retrospect I kinda wish I had gotten one because I do not want to have to run raid or pay boucoup dollars for a raptor for increased disk performance.  A perpendicular drive seems like a nice compromise.

---

### Post by information_entropy on 2008-01-14
> **logos34 said:**
>  .. and quite a few people complained about 'chatter' and heat  ...

My Seagate Barracuda  SATA 3.0Gb/s 320-GB Hard Drive is so quiet I thought it was broken when I first got it.
Drive feels to be about room temperature right now. (Stick hand in case,  feel drive test)

I get 73.05 MB/sec from the 320 drive

A computer with insufficient memory for what it is trying to do, a poorly placed swap file,
or a randomly placed and possibly fragmented swap file like some other OS,
may result is a system that sounds like those wind up gag chattering teeth, and runs hot.

Memory size and swap file placement make a significant difference in how much drive noise a computer makes

---

### Post by logos34 on 2008-01-14
> **information_entropy said:**
> My Seagate Barracuda  SATA 3.0Gb/s 320-GB Hard Drive is so quiet I thought it was broken when I first got it.
Drive feels to be about room temperature right now. (Stick hand in case,  feel drive test)

I get 73.05 MB/sec from the 320 drive

A computer with insufficient memory for what it is trying to do, a poorly placed swap file,
or a randomly placed and possibly fragmented swap file like some other OS,
may result is a system that sounds like those wind up gag chattering teeth, and runs hot.

Memory size and swap file placement make a significant difference in how much drive noise a computer makes

yeah, maybe thrashing was the issue.

---

### Post by dutchcow on 2008-01-14
My laptop sata drive could also be tad bit faster i suspect, it also runs very hot, 49 degrees idle and upto 65 when its working. But that could be the drive itself or laptop build (v3000 HP/Compaq) and not ubuntu. Drive is a Fujitsu MHV2060BH, 5400rpm 60GB. 

```

# hddtemp /dev/sda
/dev/sda: FUJITSU MHV2060BH PL: 49 C

# hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads:   1230 MB in  2.00 seconds = 615.11 MB/sec
 Timing buffered disk reads:  118 MB in  3.02 seconds =  39.09 MB/sec

 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

```

Is this speed correct and/or can i gain some speed increase with some tweaking?

---

### Post by articpenguin on 2008-01-14
raptors are you talking about the raptors with clearcase windows that are 10000RPM?

---

### Post by fjgaude on 2008-01-14
All these reports are very interesting. My laptop has a 160G Samsung in it, 5400RPM, that reading 54MB/sec under 7.04, 32-bit, using hdparm. Now under 7.10, 64-bit it reads only 35. Hmmm. I pretty sure it is a perpendicular drive.

On my main box, I had four WD Raptor 36GB drives that tested at 44MB/sec each. Two in software raid0 came in at 80; three, at 114; four, at 104. Determined throughput was limited by the PCI bus SATA controller.

Later, present time, went to 300GB Seagates, perpendicular, and they each measure at 77MB/sec. Put three of them in raid5 and get 114MB/sec; four, at 102. Same issue, PCI bus of 133MB/sec limitation.

I'm getting ready for a new MB with SATA controller on PCI-Express X1 bus. That's good for 500MB/sec so my raid5 will go up to about 210MB/sec througput under hdparm -t.

Let the good times roll.

---

### Post by mister_pink on 2008-01-14
```
hddtemp /dev/hdb
/dev/hdb: SAMSUNG SV0813H: 250°C
```

Oh dear... ;)

---

### Post by logos34 on 2008-01-14
> **mister_pink said:**
> ```
hddtemp /dev/hdb
/dev/hdb: SAMSUNG SV0813H: 250°C
```

Oh dear... ;)

hah...should be glowing like a hot coal.

---

### Post by peabody on 2008-01-14
I'd be curious about this myself.  I never had windows or a different version of Linux running on this laptop.  It's a compaq presario c571nr.  Seems to be sporting [this](http://www.excelcomputerinc.com/partpicture_EX.asp?ref=798&category=drives) hard drive.  hdparm seems to give me about 42.56 MB/sec.  I always thought that might be a little slow.  I wonder if there would be a way for me to test this with some other live CD such as Knoppix?

---

### Post by logos34 on 2008-01-14
> **fjgaude said:**
> All these reports are very interesting. My laptop has a 160G Samsung in it, 5400RPM, that reading 54MB/sec under 7.04, 32-bit, using hdparm. Now under 7.10, 64-bit it reads only 35. Hmmm. I pretty sure it is a perpendicular drive.  

On my main box, I had four WD Raptor 36GB drives that tested at 44MB/sec each. Two in software raid0 came in at 80; three, at 114; four, at 104. Determined throughput was limited by the PCI bus SATA controller.

Later, present time, went to 300GB Seagates, perpendicular, and they each measure at 77MB/sec. Put three of them in raid5 and get 114MB/sec; four, at 102. Same issue, PCI bus of 133MB/sec limitation.

I'm getting ready for a new MB with SATA controller on PCI-Express X1 bus. That's good for 500MB/sec so my raid5 will go up to about 210MB/sec througput under hdparm -t.

Let the good times roll.

Very interesting...So it's the PCI bus that's the bottleneck?  Are all new boards switching the sata controller to the PCI-Express bus?

35 is pretty low...something is really wrong.  Did you run the test several times in succession?

Has anyone tried using **blktool** to tweak their sata drives?

---

### Post by fjgaude on 2008-01-14
> **logos34 said:**
> Very interesting...So it's the PCI bus that's the bottleneck?  Are all new boards switching the sata controller to the PCI-Express bus?

35 is pretty low...something is really wrong.  Did you run the test several times in succession?

Has anyone tried using **blktool** to tweak their sata drives?

I moved over from mainbox to laptop to run tests:

```
/dev/sda1:
 Timing cached reads:   1622 MB in  2.00 seconds = 810.71 MB/sec
 Timing buffered disk reads:  102 MB in  3.01 seconds =  33.88 MB/sec
frank@moonlight:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1608 MB in  2.00 seconds = 804.51 MB/sec
 Timing buffered disk reads:  114 MB in  3.04 seconds =  37.55 MB/sec

frank@moonlight:~$ sudo hddtemp /dev/sda
[sudo] password for frank:
/dev/sda: SAMSUNG HM160JI: 43°C
frank@moonlight:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1664 MB in  2.00 seconds = 831.95 MB/sec
 Timing buffered disk reads:  110 MB in  3.02 seconds =  36.36 MB/sec
```

The temp is to show others my Samsung perpendicular. Notice my signature. <smile>

Yes, AFAIK, all the new MBs are using the PCI-E bus for their raid, SATA controllers at X1, which should make them really fast for fakeraid or as just controllers.

---

### Post by nitromanrc on 2008-03-22
MUAHAHA i own you guys...i have a Seagate Barracuda 7200.10 250 GB..and here's my hdparm -t ```
/dev/sda:
 Timing buffered disk reads:  260 MB in  3.01 seconds =  86.32 MB/sec

```

although...i am running Debian...that may make the difference

---

