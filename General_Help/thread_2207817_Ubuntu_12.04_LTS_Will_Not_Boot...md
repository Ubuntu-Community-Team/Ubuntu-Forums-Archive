---
title: "Ubuntu 12.04 LTS Will Not Boot..?"
date: 2014-02-25
forum: General Help
---

### Post by william19 on 2014-02-25
Hi,

I am fairly new to Ubuntu, so bear with me. I wanted to get into Linux by putting it on my old Dell Inspiron 700m. The laptop's hard drive failed a few years back so I removed it and put an external hard drive in which Linux was to be installed on. I created a separate 20gb partition on the external hard drive for Ubuntu 12.04. Then I got Ubuntu 12.04 LTS non-PAE 32-Bit on a flash drive via YUMI. The live test version of Ubuntu worked fine, and installation onto the prepared partition went smooth too. The problem began when I restarted the computer and a command prompt line appeared blinking in the top left corner of the screen. I tried typing something in, but nothing appeared leading me to believe the computer could not find Linux. I immediately went into the Bios and changed the boot order so that my external hard drive was first, and still nothing. I reformatted the drive and tried the same process with Linux Mint 13 Maya MATE 32-Bit and got the same result. So, is there anything I did wrong, or is there a hardware or software problem?

 Basic Dell Inspiron 700m specs:
512mb DDR1 Ram
1.6 Ghz Pentium M Dothan
Seagate External USB HDD 640Gb

---

### Post by TheFu on 2014-02-25
Common issue. 
Did this system ever boot 12.04 before?
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)
and running **boot-info** (see my signature for links).

---

### Post by stalkingwolf on 2014-02-25
where did it install grub to?  make sure it is installing to the external drive.

---

### Post by william19 on 2014-02-25
I got the boot-repair and it fixed it! Thank you guys so much, now I have to figure out how to mark this thread as solved XD. Thanks again you guys saved my old laptop!

---

### Post by bc.haynes on 2014-02-25
Go to your first post and under "Thread Tools", select "Mark this thread solved."

---

