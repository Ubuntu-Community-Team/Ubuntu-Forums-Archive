---
title: "No decrypted files in /tmp/ecryptfs.XXXX after decryption"
date: 2016-11-26
forum: General Help
---

### Post by cheniek0001 on 2016-11-26
Hi, I encrypted my home directory with previous installation of ubuntu (it was distrib. based on 14.04). Now I have installed Ubuntu 16.04. I've been trying decrypt files from my old /home directory  with command in terminal: ecryptfs-recover-private /path to /.private folder/. After entering a command I was asked and did as follow 

```
INFO: Found [/home/pablo/.ecryptfs].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [4c1e3d99eb04a245] into the user session keyring
INFO: Success!  Private data mounted at [/tmp/ecryptfs.xxxxxx].
```

Great, but when navigate even as root in Nautilus to that directory, there are only 5 files: auto-mount, auto-umount, Private.mnt, Private.sig, wrapped-passphrase. No any directory, anything. What is wrong, what should I do?

I've found the solution. I navigated previously to other directory which was also encrypted   (was containing .private directory) but was in fact empty. That is why there was no directories in /tmp. No I've found correct encypted /home directory and there are  my files in /tmp.

---

