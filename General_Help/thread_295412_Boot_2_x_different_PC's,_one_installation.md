---
title: "Boot 2 x different PC's, one installation"
date: 2006-11-08
forum: General Help
---

### Post by casperl on 2006-11-08
Hi all, this is my requirement: 

I need to commute with 1 removable ATA drive and boot up either of two different PC's  from this one installation of Xubuntu.  The same basic installation of Ubuntu has to boot up from either machine.

OK, the reason is that 1 machine is on a distant farm in South Africa that does not even have copper telephone lines to the farm, let alone any other sort of electronic communication!  Periodically, around once a week that particular Ubuntu installation has to be connected to the Internet in the local town for communication purposes.

Can this be done?  How?

Currently, either machine will boot up from the same HDD with x386 Linux.  Of course the current conflict is with the different graphics card on the second PC causing various X-Windows errors.  Sound hardware is external USB but it is not important if it does not work.  Of course the chipsets on the motherboards differ as well, but I could not see problems so far.

How do I do it?  In the interest of RTFM, I perused the Grub documentation with the result that I am now thoroughly and utterly confused.

A second alternative arrangement is for a second (permanent) Linux hard drive to exist on either PC and to store the home dir and all the MySQL tables on the removable drive.  

A third alternative is for two partitions to be created for each PC to boot up (VIA grub) and a third partition containing common data.

The second and third alternatives have the major drawback that everything has to be installed twice etc.

Any advice will be appreciated!

---

### Post by dcstar on 2006-11-08
> **casperl said:**
> 
.......
Currently, either machine will boot up from the same HDD with x386 Linux.  Of course the current conflict is with the different graphics card on the second PC causing various X-Windows errors.  Sound hardware is external USB but it is not important if it does not work.  Of course the chipsets on the motherboards differ as well, but I could not see problems so far.

How do I do it?  In the interest of RTFM, I perused the Grub documentation with the result that I am now thoroughly and utterly confused.
.......

Any advice will be appreciated!

Select the "vesa" option in the xorg configuration, that should work with all video cards (albeit non-optimum performance).

Do a forum search on how to reconfigure xorg and you should get some usable instructions that may fix one of the issues.

---

### Post by casperl on 2006-11-09
Thanks!

Selecting VESA worked perfectly in XORG.  Both machines now boot up like a dream without needing any other major settings, and this really makes a massive difference.

There is a substantial market for exactly this solution in the third world where effective Internet access is either non-existent or at a premium.  With the proper management, a farmer, a school or even small businesses can take their removable hard drive to a central location that has broadband access and retrieve email, albeit a few days late, download web pages, syncronise databases and upload information to the Internet.

The ease with which this normally impossible task has been achieved in Xubuntu totally blows me out of the water.

Again, this opens up a totally new horizon for applying Ubuntu in places where it will really make a difference in people's lives.  I certainly do my bit to promote this solution.

---

