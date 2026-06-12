---
title: "Can't recover encrypted home drive"
date: 2013-11-13
forum: General Help
---

### Post by akgrant on 2013-11-13
Hi,


I rebooted my 13.04 laptop this morning and can no longer access my home drive.


This was an encrypted drive set-up during installation, and I recorded the encryption key.


I don't believe I've done anything that might have caused the corruption, other than the usual Ubuntu upgrades.  I'm haven't changed any passwords since the install, and I'm fairly confident that I've typed in the correct passwords.


What I've seen so far:


Logging on to tty1 shows no files in my home drive. Normally accessing the home directory without mounting the private file system shows two files (Access-Your-Private-Data.desktop and README.txt, I believe).


Attempting to mount the encrypted drive fails:


```
$ ecryptfs-add-passphrase --fnek
Passphrase: 
Inserted auth tok with sig [3eed69179f8d5e61] into the user session keyring
Inserted auth tok with sig [73f299915ebec587] into the user session keyring


$ sudo mount -t ecryptfs /mnt/disk1/home/.ecryptfs/alistair/.Private /mnt/disk2
[sudo] password for alistair: 
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32
 2) blowfish: blocksize = 8; min keysize = 16; max keysize = 56
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: 
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [3eed69179f8d5e61]: 73f299915ebec587
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=73f299915ebec587
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=3eed69179f8d5e61
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.


Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [3eed69179f8d5e61] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
mount: No such file or directory
Error mounting eCryptfs: [-1] Operation not permitted
Check your system logs; visit <http://ecryptfs.org/support.html>



```





Attempting to recover the passphrase with encrypt-unwrap-passphrase fails:


```
$ ecryptfs-unwrap-passphrase /mnt/iso/home/.ecryptfs/alistair/.Private
Passphrase: 
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs



```/var/log/syslog:


```
Nov 14 14:03:24 alistair-srv ecryptfs-unwrap-passphrase: Error attempting to rea
d encrypted passphrase from file [/mnt/iso/home/.ecryptfs/alistair/.Private]; si
ze = [4294967295]



```
Help :-)

Thanks,
Alistair

---

### Post by TheFu on 2013-11-14
Ouch.  Every hard drive will fail. If not today then eventually. We hope to get 4-8 yrs of use most of the time, but nothing is guaranteed.  I've had drives fail after 2 days, 6 months, 1 yrs and I have some running fine after 8 yrs. We never know when a HDD is going to fail.

I would start by using **ddrescue** to mirror the /home partition completely. Let it get as much of the data as possible onto a fresh, known-working HDD.  Then I would only work on the cloned data, never the original.

You have probably seen this article: [http://www.howtogeek.com/116297/](http://www.howtogeek.com/116297/) on how to recover an encrypted HOME.  If there is disk corruption, you may be screwed.  I hope only a few files are lost, not the most critical parts, so some of the data might be restored.  The **sudo ecryptfs-recover-private** run from a liveCD seems to be their trick. A few comments say it didn't work, however.

So, how are your backups?  Running with encryption means having 100% perfect, know-you-can-recover backups.  The only solution I know to the unpredictable nature of HDD failures is good backups.  With encryption, either having no important data on the HDD or having fantastic, automatic, daily backups is my rule.  

Of course, if you have backups, just restore.

---

### Post by akgrant on 2013-11-15
Thank you!


ecryptfs-recover-private was able to get back everything.  I had actually seen this utility when I was searching, but for some reason had the impression that it needed ecryptfs-unwrap-passphrase to be successfully run first (which I hadn't been able to do).


Thanks again,
Alistair

P.S. I did take an image of the disk with ddrescue, and have a backup which is about 3 days earlier than the failure, but it's much nicer to have everything up to the minute.

---

