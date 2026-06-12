---
title: "Ubuntu v5.10 LiveCD locks up at Enterprise Volume Management System"
date: 2005-10-29
forum: General Help
---

### Post by eternal0void on 2005-10-29
I recently handed out Ubuntu "Breezy" v5.10 LiveCDs at a technology expo booth for my local Linux User Group (PC x86 LiveCDs) .  We also handed out business cards for the LUG and how to get on our mailing list.  One day after the expo we received this E-mail on our mailing list:

===================

[original user email info removed]

  The Linux Live CD locked up on my XP PC on bootup at the 
  following line:

     Starting Enterprise Volume Management System

  The CD is the Ubuntu v. 5.10 LinuX LiveCD. The HW 
  configuration is an IBM clone, Intel P4 2.6 GHz 
  hyperthreading processor (hyperthreading enabled in BIOS) 
  on an Intel motherboard, 1GB 133 Mhz DDR RAM, with an 
  Nvidia video card, 1 standard CDROM drive, 1 DVD+RW drive 
  (Linux CD was used in standard CDROM drive) and 2 HD's: 
  One 20 GB with 1 partition + one 100 GB with 2 partitions; 
  SW configuration is Win XP SP-2.

===================

Any ideas on what could be causing the problem?  Is there an Ubuntu "cheat code" to disable EVMS?

My LUG was delighted to find that the Ubuntu v5.10 LiveCD also contained Windows installers for several Windows OSS applications (OpenOffice.org, Firefox, etc.), but if this is a common error then we may go back to handing out two CDs instead (KNOPPIX and a Windows OSS applications CD).

---

### Post by vayu on 2005-10-30
[QUOTE=eternal0void]
  The Linux Live CD locked up on my XP PC on bootup at the 
  following line:

     Starting Enterprise Volume Management System

 Any ideas on what could be causing the problem?  Is there an Ubuntu "cheat code" to disable EVMS?

[/QUOTE]

That happened to me too.  I booted into recoverymode and it was able to get past that point.  Then at the command prompt I disabled the starting of that service with:
update-rc.d -f evms remove

---

### Post by giggss on 2005-10-30
i have exactly the same problem. can anyone advise on how to solve this?

---

### Post by giggss on 2005-10-30
[QUOTE=vayu]That happened to me too.  I booted into recoverymode and it was able to get past that point.  Then at the command prompt I disabled the starting of that service with:
update-rc.d -f evms remove[/QUOTE]
how to boot in recovery mode using the Live CD?

---

### Post by eternal0void on 2005-10-30
[QUOTE=vayu]That happened to me too.  I booted into recoverymode and it was able to get past that point.  Then at the command prompt I disabled the starting of that service with:
update-rc.d -f evms remove[/QUOTE]
Does the LiveCD have a "recovery mode"?  I was under the impression that the LiveCDs in general do not have "recovery mode".  More to the point, you cannot modify rc.d on a read-only CD filesystem.

---

### Post by pchachte on 2005-10-30
I get this error about once a month or two.  Whenever it happens, I just turn off the computer, reboot, and everything is fine when I start up the next time.  It's a little disconcerting, but so far it hasn't caused any real problems.

Would be nice to fix it though.

---

