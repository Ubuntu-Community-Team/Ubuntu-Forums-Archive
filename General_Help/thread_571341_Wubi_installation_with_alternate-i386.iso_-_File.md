---
title: "Wubi installation with alternate-i386.iso - File"
date: 2007-10-09
forum: General Help
---

### Post by Joss74 on 2007-10-09
hi, 
I placed Wubi-7.04.04.exe and ubuntu-7.04-alternate-i386.iso in the same folder.
After beginning of installation Wubi says "Extracting c:\wubi-install\ubuntu-7.04-alternate-i386.iso to d:\wubi"
and have copied files (~10 MB ) to D:\wubi. 
But after that the ubuntu-7.04-alternate-i386.iso vanished 
and ubuntu tryed to download online! (but on this machineI havn't internet access)
Whats wrong with that?!
Hope for help, thanx,
josch

---

### Post by ago on 2007-10-09
> **Joss74 said:**
> hi, 
I placed Wubi-7.04.04.exe and ubuntu-7.04-alternate-i386.iso in the same folder.
After beginning of installation Wubi says "Extracting c:\wubi-install\ubuntu-7.04-alternate-i386.iso to d:\wubi"
and have copied files (~10 MB ) to D:\wubi. 
But after that the ubuntu-7.04-alternate-i386.iso vanished 
and ubuntu tryed to download online! (but on this machineI havn't internet access)
Whats wrong with that?!
Hope for help, thanx,
josch

The file was probably moved to /wubi/install/
Wubi performs a checksum on the file. If that is not correct (which indicates a corrupted download) it will try to download the file again.
You can run a checksum yourself and check against the one in the corresponding metalink file

---

### Post by Joss74 on 2007-10-11
@ago: Thank you for the hint - you was all right - my first alternate-i386.iso had a wrong checksum!
Now the installation runs very well :)
j.

---

