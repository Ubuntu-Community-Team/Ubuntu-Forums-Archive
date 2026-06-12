---
title: "GnuPG"
date: 2008-01-22
forum: General Help
---

### Post by DapperMe17 on 2008-01-22
When encrypting a file to a "shared" (Windows/Ubuntu dual boot fat32 shared file) with Kgpg (GnuPG) in Kubuntu, the file extension is .asc. 

Using GPGee (GnuPG frontedn for Windows), I can't decrypt the file. 

However, when I encrypt a file with GPGee in Windows, it uses the .gpg extension. I have no problem decrypting this file with Kgpg in Kubuntu.

Any idea why I can't decrypt the opposite way, Kgpg (Kubuntu) file with GPGee (Windows)?

---

### Post by kevdog on 2008-01-22
Hmm .gpg extensions meaning you are using a binary encryption. The .asc means ascii armored.  Either way both files should work bidirectionally unless your keys are not setup appropriately.

---

