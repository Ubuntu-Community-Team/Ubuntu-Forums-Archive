---
title: "curlftpfs mount ftp, symlinks not working"
date: 2012-12-13
forum: General Help
---

### Post by mudflapz on 2012-12-13
I'm using curlftpfs to mount an ftp to my local drive.  Works fine except symlinks.  When ever I click on one in the file manager it doesn't work.  Here is the curlftpfs code I use:
```
sudo curlftpfs -o allow_other,transform_symlinks  USER:PASSWORD@SERVER /home/matt/ftp_test/
```

I've tried this on xubuntu 64 12.04 and xubuntu 32 12.10.  Same outcome.

---

