---
title: "Freeze or Reboot running ubuntu 7.10"
date: 2008-02-23
forum: General Help
---

### Post by mgd on 2008-02-23
Greetings, 

I am trying to refrubish/resue some old PC systems that had been used in my SETI farm.  These systems ran the SETI client under RedHat 7 (or, in some cases, RedHat 9).  

I am having problems with 2 of these systems that have Radisys motherboard with Intel Pentium III 600 MHz; 256MBy RAM; 5.1GBy HDD; CD-RW.  

The ubuntu install runs OK.  

Sometimes during boot, the system will reboot (POST messages show); sometimes the system will run OK for a while then reboot; sometimes the system will freeze.  

I have run memtest for 24 hours w/o any error.  

I have moved the HDD (with ubuntu installed) into another case w/ the same motherboard ... also same CD; Video; and network card ... same kind of errors on both boxes.  

Suggestions ... please ... 

--
mgd

---

### Post by Gen2ly on 2008-02-23
Take a look at the file [COLOR="SeaGreen"]/var/log/messages[/COLOR] and see if any problems exist with hardware.  If the PC is only up for little tlme copy the file to usb disk or another pc.  Also take a look a dmesg.  It can be put to file with:

```
dmesg > hardware-information.txt
```

And again look for hardware issues.  Also taking look at the X server log my help too

```
cat /var/log/Xorg.0.log | grep -B 2 - A 2 EE
```

---

### Post by mgd on 2008-02-23
I appreciate that **Dirk.R.Gently** offered some suggestions to check for hardware errors.  

I would probably need to use a FDD to capture any error information ... how do I mount a FDD for writing?  

Thanks for any advice ... 

-- 
mgd

---

