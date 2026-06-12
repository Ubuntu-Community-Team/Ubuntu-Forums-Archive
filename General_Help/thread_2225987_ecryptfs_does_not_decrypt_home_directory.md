---
title: "ecryptfs does not decrypt home directory"
date: 2014-05-24
forum: General Help
---

### Post by zaphod_es on 2014-05-24
I just got back from holiday and booted the laptop after a month of inactivity.  It did not offer me my usual login, only the alternative username.  It did not take me long to work out that there is a glitch in the decryption of my home directory.

Running sudo ecryptfs-recover-private shows the data is all there and not corrupted. (See below)
So it appears that it is an Ubuntu startup configuration problem rather than a ecryptfs problem.

I would appreciate some help restoring the setup so that, on bootup, the drive is automatically decrypted and and be able to log in under my usual username. There are good backups so this is not a recovery problem, just getting back to where I was without lots of file copying etc.

Ubuntu 12.04 64 bit.

ZB

sudo ecryptfs-recover-private
[sudo] password for user: 
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/home/.ecryptfs/username/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [c15760b0b8111f5b] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.uJJLNPpv].

---

