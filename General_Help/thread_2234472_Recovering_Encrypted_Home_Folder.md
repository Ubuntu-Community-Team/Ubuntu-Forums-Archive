---
title: "Recovering Encrypted Home Folder"
date: 2014-07-14
forum: General Help
---

### Post by wizard135 on 2014-07-14
After a borked upgrade from 13.10 to 14.04, I fsync'ed my previous (encrypted) home folder to an external drive and restarted with a fresh instal of 14.04. How can I recover this data? I don't have the passphrase, although I do remember the old login password. I still have the "wrapped-passphrase" and ".wrapped-passphrase.recorded" files, under [externaldrive]/home/.encryptfs/[username]/.encryptfs/, although tutorials I have attempted have failed so far...

---

### Post by Whoopie on 2014-07-15
Try the attached script. You have to adjust the variables ROOT and TARGET.

```

#!/bin/sh

ROOT=/tmp/backup/mnt/.ecryptfs/whoopie
TARGET=/tmp/backup/user/home/whoopie

# ROOT should be the parent of the .ecryptfs and .Private folders

mkdir -p $TARGET
cd $ROOT

echo Type your password:
PASS=$(ecryptfs-unwrap-passphrase .ecryptfs/wrapped-passphrase | sed s/Passphrase:\ //)
SIG1=$(head -n1 .ecryptfs/Private.sig)
SIG2=$(tail -n1 .ecryptfs/Private.sig)

echo Passphrase:
echo $PASS
echo Signatures:
echo $SIG1
echo $SIG2

echo Should be empty:
keyctl clear @u
keyctl list @u

echo Do not type anything:
echo $PASS | sudo ecryptfs-add-passphrase --fnek

echo Sould have signatures:
keyctl list @u

echo Mounting $ROOT on $TARGET...
mount -t ecryptfs -o key=passphrase,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_passthrough=no,ecryptfs_enable_filename_crypto=yes,ecryptfs_sig=$SIG1,ecryptfs_fnek_sig=$SIG2,passwd=$(echo $PASS) $ROOT/.Private $TARGET

ls $TARGET

```

---

### Post by wizard135 on 2014-07-15
Thank you, so so much

---

### Post by sedawk on 2014-07-17
You can recover the "real" passphrase with tool ecryptfs-unwrap-passphrase and the old wrapped-passphrase file:
ecryptfs-unwrap-passphrase wrapped-passphrase
This tool will ask for "passphrase" which in this case is the same as "login passphrase" which actually is the old login password.

---

