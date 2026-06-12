---
title: "Flash Drive Encrypted w/TrueCrypt - will I have access on Windows Machine?"
date: 2014-04-22
forum: General Help
---

### Post by johnsmoke on 2014-04-22
So I'm getting a new flash drive, and I'm excited because this time I can finally encrypt it, like I should have with my old one. I was wondering, if I format it with NTFS and encrypt it with TrueCrypt in Ubuntu, will I be able to plug the drive into any windows machine and access it also?

---

### Post by sandyd on 2014-04-22
> **johnsmoke said:**
> So I'm getting a new flash drive, and I'm excited because this time I can finally encrypt it, like I should have with my old one. I was wondering, if I format it with NTFS and encrypt it with TrueCrypt in Ubuntu, will I be able to plug the drive into any windows machine and access it also?

Yes you should - if the windows computer has truecrypt installed.

---

### Post by johnsmoke on 2014-04-22
> **sandyd said:**
> Yes you should - if the windows computer has truecrypt installed.


Ok, great, thanks! Also, can't I just have the exe file for TrueCrypt on the thumb drive itself so that TrueCrypt doesn't even need to be physically installed on the windows machine? If so, I would just download the exe file for TrueCrypt and drag it onto the flash drive? Could even do this within Ubuntu?

---

### Post by oscarivera9 on 2014-04-22
> **johnsmoke said:**
> Ok, great, thanks! Also, can't I just have the exe file for TrueCrypt on the thumb drive itself so that TrueCrypt doesn't even need to be physically installed on the windows machine? If so, I would just download the exe file for TrueCrypt and drag it onto the flash drive? Could even do this within Ubuntu?

There are two ways to encrypt your flash drive.
[LIST=1]
[*]You can encrypt the whole flash drive, in which case you would need TrueCrypt installed in both computers that you'll use to access the flash drive.
[*]You can create an encrypted container within the flash drive and leave some empty space in the flash drive so that you can store TrueCrypt there (outside of the container you created but in the flash drive).  Having stored TrueCrypt AND the encrypted container in the flash drive separately you can then use the **TrueCrypt Portable Mode** to decrypt the container:
[/LIST]
[http://www.truecrypt.org/docs/truecrypt-portable](http://www.truecrypt.org/docs/truecrypt-portable)

---

### Post by drac-noc on 2014-04-23
Another method is to partition the flash drive, allow yourself roughly 50Mb for a regular FAT32 partition so it can openly store any versions of TrueCrypt you need to use, and allow the rest for the encrypted volume you want to create. 

TrueCrypt is perfectly happy to handle a partition as a "whole device", so you should get the best of both worlds.

---

### Post by johnsmoke on 2014-04-24
> **oscarivera9 said:**
> There are two ways to encrypt your flash drive.
[LIST=1]
[*]You can encrypt the whole flash drive, in which case you would need TrueCrypt installed in both computers that you'll use to access the flash drive. 
[*]You can create an encrypted container within the flash drive and leave some empty space in the flash drive so that you can store TrueCrypt there (outside of the container you created but in the flash drive).  Having stored TrueCrypt AND the encrypted container in the flash drive separately you can then use the **TrueCrypt Portable Mode** to decrypt the container: 
[/LIST]
[http://www.truecrypt.org/docs/truecrypt-portable](http://www.truecrypt.org/docs/truecrypt-portable)


Thanks much for the advice. So, I understand creating the container/volume. I guess I'd also have to do the "Travelers Disk" thing they have listed there, and that's what adds the exe program outside the container? I can't tell if that's what does that or if I just drag the exe file into the flash drive (outside the container) and I'm good to go?

---

### Post by johnsmoke on 2014-04-24
Never mind, it looks like I do create the "Traveler Disk" to make this portable to use in Windows Machines. Good instructions here on the whole process - [http://www.howtogeek.com/61810/how-to-protect-your-flash-drive-data-with-truecrypt/ ]("http://www.howtogeek.com/61810/how-to-protect-your-flash-drive-data-with-truecrypt/")

---

