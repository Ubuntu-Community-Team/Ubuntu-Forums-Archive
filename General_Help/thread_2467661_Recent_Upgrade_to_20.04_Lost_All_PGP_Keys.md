---
title: "Recent Upgrade to 20.04 Lost All PGP Keys"
date: 2021-10-03
forum: General Help
---

### Post by jdmtimemachine on 2021-10-03
Hi everyone, recently did a fresh install of 20.04 after running 16.04 for awhile.

Was very happy with the install, everything ran so smoothly until i plugged in my encrypted flash drive to use my gpg4usb program.

For some reason all the PGP keys were wiped clean, i couldn't even import/generate a new key.

I thought installing Unity desktop environment would help because 16.04 was running that, but that didn't help at all.

All in all VERY happy with 20.04, feels very polished and works great, but seeing all my keys wiped from everything was a kick in the butt i was not expecting.

Would anyone know as to why something like this would have happened? 

It's as though i'm missing a program in 20.04 that was running in my old 16.04 that made PGP possible.

I was almost tempted to reinstall 16.04 and are still tempted so i can retain all the keys that have been lost, but that's my final option and i will do that in case i can't find a work around.

Any help would be greatly appreciated in regards to recovering my lost pgp keys.

I feel as though the program simply wont work with new distros, weird but could be the case.

Thanks everyone.

---

### Post by grahammechanical on 2021-10-03
What kind of fresh install of 20.04 did you do? Was it the kind that formatted the partition and erased everything on the partition? If you have wipeout your personal folders and files, the ones in /home/username then re-installing 16.04 will not solve the problem.

Your public keys are stored here

[https://keyserver.ubuntu.com/](https://keyserver.ubuntu.com/)

Where your private key is stored on your machine I cannot say. I have only used PGP once and that was to sign the Ubuntu Code of Conduct. And that was years ago and a lot has happened to me since then.

Regards

P.S. I think that you will find that GPG is installed by default on 20.04.

[http://manpages.ubuntu.com/manpages/xenial/man1/gpg.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/gpg.1.html)

---

### Post by jdmtimemachine on 2021-10-04
Hi, yes it erased previous version of Ubuntu so wiped previous files.

Yes your right about 16.04, i installed VirtualBox and ran 16.04 within that and it made no differnce.

Sadly i didn't have my key stored on Ubuntu server, i was using the gpg4usb program which ran from my usb drive.

I installed the GPG and created a key, but it has no function to be able to decrypt other PGP/GPG messages that i can see..

---

### Post by Dennis N on 2021-10-04
> **jdmtimemachine said:**
> Hi, yes it erased previous version of Ubuntu so wiped previous files.

Yes your right about 16.04, i installed VirtualBox and ran 16.04 within that and it made no differnce.

Sadly i didn't have my key stored on Ubuntu server, i was using the gpg4usb program which ran from my usb drive.

I installed the GPG and created a key, but it has no function to be able to decrypt other PGP/GPG messages that i can see..

gpg is a command line tool that by itself can encrypt and decrypt files but requires some study of the relevant commands. 

Your gpg4usb sounds like a tool that does the actual encryption or decryption for you but uses keys stored on your computer, eliminating the need to learn any gpg commands and options. Doing a fresh install would destroy those keys, unless you had exported them. Any keys you create should be exported to a backup location (like a USB drive) soon after creation, because of this.

Other Comments: 
there is a ~/.gnupg folder on your computer that is the location of keys and some other necessary files.
if you use Ubuntu, the File manager (a.k.a. Nautilus) can encrypt and decrypt files using your keys provided you have the seahorse-nautilus plugin.

---

### Post by jdmtimemachine on 2021-10-04
Hi Dennis, actually all the keys were stored on the encrypted usb drive, nothing was ever stored on Ubuntu itself.

So i was shocked when i simply plugged my usb drive in and when i clicked on my PGP program all the keys were gone, and then unable to use the program at all.

I can't even create a new key with it. I thought running 16.04 in a VM would have worked.

I have the seahorse plugin working, managed to create a key but i still can't work out how to actually use it, 

Its nothing like the gpg4usb program i was using, i see no window to enter a PGP and then de-crypt it, i must be running the wrong program.

I had better look on youtube for i can't wrap my head around it. 

Its just a very strange thing that has happened.

---

### Post by dragonfly41 on 2021-10-05
I don't know if this is relevant but in Thunderbird I installed an OpenPGP extension, way back.

I look now in Thunderbird > Tools and I have OpenPGP Key Manager.

when I launch this tool I see in toolbar > Keyserver > Discover Keys Online

---

### Post by jdmtimemachine on 2021-10-13
Apologies for late reply, but i manged to retrieve my old PGP key.

I simply took my USB to a friends laptop which was originally an Apple laptop, but i installed Ubuntu 16.04 on it a few years ago and happily wiped mac clean off it. 

Plugged my usb in and that PGP program worked perfectly so i was able to copy everything, most importantly my secret key.

I ended up using Kleopatra..i worked out how to decrypt but unable to encrypt, but the decrypt was the most important and i achieved that, but wow when you press encrypt it either does nothing or it's sending the encrypted message somewhere i can't see yet. :P

Such a shame such a well known and used program fails to work in a new Ubuntu install, that really blew my mind.

Will eventually work it out, many thanks for the help. : )

---

### Post by jdmtimemachine on 2021-10-13
> **dragonfly41 said:**
> I don't know if this is relevant but in Thunderbird I installed an OpenPGP extension, way back.

I look now in Thunderbird > Tools and I have OpenPGP Key Manager.

when I launch this tool I see in toolbar > Keyserver > Discover Keys Online

Ah yes Thunderbird!

You just reminded me of something thank you, that program will come in handy, funny thing i have never used it but will now many thanks!

---

