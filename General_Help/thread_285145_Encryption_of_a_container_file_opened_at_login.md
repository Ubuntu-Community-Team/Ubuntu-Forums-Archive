---
title: "Encryption of a container file opened at login?"
date: 2006-10-26
forum: General Help
---

### Post by MagnusL on 2006-10-26
Hi!

I am trying to set up an encrypted container file (not a partition) that I would like to be opened at boot or login, that is, asking me for the passphrase. I'm running dapper. 

I am using dmcrypt, follwing the instructions on: 
[http://deb.riseup.net/storage/encryption/dmcrypt/](http://deb.riseup.net/storage/encryption/dmcrypt/)
[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

It all works well to the point where I have an encrypted file mounted as a loopback device on /dev/loop/0, and I have created a cryptodevice called mycrypt. I can mount and open it from the command line or by executing the following script as sudo: 

 #!/bin/sh
 losetup /dev/loop/0 /home/safe
 cryptsetup create mycrypt /dev/loop/0
 mount /dev/mapper/mycrypt /home/magnus/Data/fcrypt 

However, I would like it to be mounted automatically. I tried adding a line in /etc/crypttab, but during boot get the error msg that it is not a block device (I guess losetup is not run by then). And if I try to run the above script via KDE Autostart of the Gnome equivalent, it is run as user and not root, so I'd need to have a way of supplying passwords. 

Does anyone else do this in some smart way? Am I trying something the wrong way? And how come I see these comments about loopback being "older" - is this a bad way of doing it?

Any advice on how to proceed is very welcome. 


Magnus L

---

