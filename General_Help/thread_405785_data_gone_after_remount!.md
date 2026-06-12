---
title: "data gone after remount!"
date: 2007-04-10
forum: General Help
---

### Post by tuaranoi on 2007-04-10
hi there,

i previously have a HDD (ntfs formatted in ubuntu) which for me to keep my files, today just reformatted my OS and try to remount the HDD with ntfs-config tools, but all the data was gone with out any sign! how can i get the data back? does ntfs-config tools format the drive before remounting it?

:confused: :confused: :(

---

### Post by WiseElben on 2007-04-10
No, ntfs-config would not reformat your drive before mounting. Make sure that the partition you're talking about really is an NTFS partition, maybe you reformatted it on accident while reinstalling your OS. By OS, do you mean Ubuntu or Windows?

---

### Post by tuaranoi on 2007-04-10
oh... actually last time i formatted the drive under ubuntu by the make ntfs command, i did not format the drive as what i notice, the OS i meant is ubuntu.

> **WiseElben said:**
> No, ntfs-config would not reformat your drive before mounting. Make sure that the partition you're talking about really is an NTFS partition, maybe you reformatted it on accident while reinstalling your OS. By OS, do you mean Ubuntu or Windows?

---

### Post by Dream. on 2007-04-10
I would imagine the only thing you can do if you accidentally reformatted the drive would be to run some data recovery software on the drive. 

I would connect the drive to a windows machine and recover the data that way. Unless someone knows of some data recovery software that will run under linux or wine??

---

### Post by tuaranoi on 2007-04-10
actually i have folder under the drive (hdd1) with soft link to the home directory of the users, i afraid it deleted everything when i format the hda1.

yeah will try that later, thanks anyway...

> **Dream. said:**
> I would imagine the only thing you can do if you accidentally reformatted the drive would be to run some data recovery software on the drive. 

I would connect the drive to a windows machine and recover the data that way. Unless someone knows of some data recovery software that will run under linux or wine??

---

