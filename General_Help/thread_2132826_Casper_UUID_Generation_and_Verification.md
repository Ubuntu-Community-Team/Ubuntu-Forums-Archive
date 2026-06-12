---
title: "Casper UUID Generation and Verification"
date: 2013-04-06
forum: General Help
---

### Post by SWUF2013 on 2013-04-06
Concerning the CASPER_GENERATE_UUID=1 item.  How do you use this to  create the "casper-uuid-generic-pae" file located in the ".disk"  directory of a live cd so that the initrd will compare the uuid to  ensure that the correct media or drive is booted from.  I haven't  figured out the correct way to handle this since no file was created in  the ".disk".

---

### Post by dino99 on 2013-04-06
what are you trying to do ?

---

### Post by SWUF2013 on 2013-04-06
Ensure that the initrd compares it's internal UUID to the UUID in the "casper-uuid-generic-pae" file located in the ".disk"  directory to ensure that correct root location is mounted.  The problem is figuring out how to generate the new UUID for the live cd I am making so that it will validate it.  The most important part is to validate the correct location for USB Live thumb drives.

I read information on a root file spoofing weakness, and I am attempting to use this to help in preventing this kind of exploit, since the system I have been working with is for forensics use.  A criminal would have a reason to use such an exploit to prevent a forensic distro from being able to read information from their system.

---

