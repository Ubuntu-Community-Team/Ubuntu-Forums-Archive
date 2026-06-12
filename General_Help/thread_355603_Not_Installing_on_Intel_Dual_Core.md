---
title: "Not Installing on Intel Dual Core"
date: 2007-02-07
forum: General Help
---

### Post by iammeagain on 2007-02-07
I have attempted to install ubuntu to a desktop with intel dual core, 2 GB of Ram, Sata hard drive. But it doesnt even boot. i tried with other distros also. Is there in particular command i need to set for booting with intel dual core?

---

### Post by Motoxrdude on 2007-02-07
Did you change your bios to boot from your CD-Rom drive?

---

### Post by glenm on 2007-02-08
What motherboard do you have?

---

### Post by iammeagain on 2007-02-09
yea i told bios to boot off cd. It isnt booting at all. Something about tty. It is a school computer so i can't try things right away on it. 

I don't know the specs right nonw ill post them asap. 

I was hopin to have it running with beryl to show off at an elective fair for school, but its too late now, we were forced to attempt and show off vista. Problem is it does like 2 sorta cool things. lols

---

### Post by iammeagain on 2007-02-09
Intel DP965LT motherboard for intel dual core
2 GB DDR2 RAM 667Mhz
INtel dual core 2.4 Ghz
250 GB SATA Hard Drive
GForce GT 512MB Nvidia graphics card.

---

### Post by glenm on 2007-02-10
I have an MSI 965P Neo motherboard ( uses the Intel 965 chipset ).  
Intel Core 2 Duo
1 GB ram
3 SATA Drives
1 IDE hard drive
1 IDE DVD burner

To obtain an IDE port this motherboard/chipset uses a JMicron chip to create the IDE port from a SATA port.

Kubuntu 6.10 (edgy) is the only distribution I have found that will install on my PC

There is a problem with the Linux Kernel before 2.6.17.  The install media will start then give you an error message that the install media can't be found. Google Linux Intel 965

Could this be part of your problem?

---

### Post by iammeagain on 2007-02-11
I get the error message "/bin/sh: can&#8217;t access tty" And it happens relativley quicly in the boot process. I did find some info on problems related to these types of motherboards i haven't read it yet though. Although i initially tried Kubuntu 6.10, ill read up and see what i can figure out. Thanx for pointin me in the right direction.

---

### Post by igknighted on 2007-02-11
Since it is a school computer, is it possible that the IT dept. has crippled the bios in some way so that you can't do that?  Our school does something similar.

---

### Post by iammeagain on 2007-03-10
> **igknighted said:**
> Since it is a school computer, is it possible that the IT dept. has crippled the bios in some way so that you can't do that?  Our school does something similar.


We special ordered it from Newegg just for our class and I was there the whole time it was being built plus no one but students have touched it. 
Our IT dept. isn't very smart anyways, I doubt they would do that. There are some just pathetic security holes they don't care to fix. lol.

---

