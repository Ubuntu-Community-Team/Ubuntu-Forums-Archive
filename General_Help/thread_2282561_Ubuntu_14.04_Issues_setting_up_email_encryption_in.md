---
title: "Ubuntu 14.04 Issues setting up email encryption in Thunderbird with Enigmail"
date: 2015-06-15
forum: General Help
---

### Post by zoidberg2 on 2015-06-15
I am having trouble setting up Email Encryption in Thunderbird using Enigmail. I created encryption keys on another Linux machine running Zorin without any issues & exported it to my external hard drive. 
 When I try to import it in to Thunderbird on this Ubuntu 14.04 machine, I go to Enigmail, Key Management, File,Import ~Files From Key. When I select the encryption keys to importfrom I get this message, 

Importing the keys failed
The key(s) were successfully imported

gpg: failed to create temporary file `/home/john/.gnupg/.#lk0x7f33b9511b50.john-desktop.8993': Permission denied
gpg: keyblock resource `/home/john/.gnupg/secring.gpg': General error
gpg: failed to create temporary file `/home/john/.gnupg/.#lk0x7f33b9513400.john-desktop.8993': Permission denied
gpg: keyblock resource `/home/john/.gnupg/pubring.gpg': General error
gpg: key 2D10E96A: no public key - can't apply revocation certificate
gpg: Total number processed: 1  I thought that the issue was that I needed my public key first so when I tried downloading it I got this error, 


gpg: failed to create temporary file`/home/john/.gnupg/.#lk0x7fc50ebfbc70.john-desktop.8335': Permission denied
gpg: keyblock resource `/home/john/.gnupg/secring.gpg': General error
gpg: failed to create temporary file `/home/john/.gnupg/.#lk0x7fc50ebfd520.john-desktop.8335': Permission denied
gpg: keyblock resource `/home/john/.gnupg/pubring.gpg': General error
gpg: requesting key 2D10E96A from hkp server pool.sks-keyservers.netgpg: no writable keyring found: Unknown system error
gpg: error reading `[stream]': General error
gpg: Total number processed: 0


Even when I run through the generate new keys option on this machine it takes hours & gives me this error message,    The key generation failed. Please check the Enigmail console (Menu Enigmail > Debugging Enigmail) for details.

---

