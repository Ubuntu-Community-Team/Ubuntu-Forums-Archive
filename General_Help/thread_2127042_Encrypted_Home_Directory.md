---
title: "Encrypted Home Directory"
date: 2013-03-18
forum: General Help
---

### Post by Gnewbie on 2013-03-18
Hi All,

When installing Ubuntu 11.10 (I believe) on my now crashed computer (likely H/W problem), I encrypted the drive during the regular installation process.  When the computer stopped working, I removed the HD and am now trying to access it as a USB drive on my new computer.

When I plug the drive in via USB, the various partitians mount, including the name of the encrypted Home drive.

I'm using a tutorial that uses a TrueCrypt GUI in order to access the drive.

[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

Will TrueCrypt work to decrypt this drive so long as I have the right password?

When I connect the USB, the various Filesystems on the drive automatically mount, including the Filesystem that contains the Home directory (along with data, dev, lost+found, proc, system).

Should I eject the Filesystem with the Home directory before trying to mount the encrypted Home Directory?

The reason I don't just don't try and decrypt the drive is because there is some trial and error involved in nailing down the exact password.  I have a good idea what it is within a limited range, but I don't know exactly what it is - so I don't know if a failure is due to the wrong password or a wrong process.

Any guidance is appreciated.

TIA...

GNewbie

---

### Post by Gnewbie on 2013-03-21
Hi All,

I'm following this tutorial to gain access to my HD.

How to Recover an Encrypted Home Directory on Ubuntu

[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

Unfortunately, I don't recall the exact password, just the general framework.  I may have to go through 100 to 200 passwords to be sure I have iot covered.  Is there any way to automate the process outlined in the tutorial?  I could put all potential variations of the password in a text file and parse through it until the password hits.  Even better, if the automation process counted how many passwords were checked before hitting pay dirt, I would know which password version was the actual password.

Any help is appreciated.

TIA...

---

