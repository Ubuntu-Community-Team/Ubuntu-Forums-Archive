---
title: "Huge Speed Difference Rsync vs Sftp?"
date: 2015-08-09
forum: General Help
---

### Post by sslx on 2015-08-09
I'm trying to sync large amount of data from Ubuntu to Windows over the internet.
If I use cwRsync 5.4.1 using the following setting,
rsync -avhPe "ssh -T -c arcfour -o Compression=no -x" user@host:/dir/ dir
I get around 550KB/s. However, if I use FileZilla with sftp connection, I can get around 10MB/s.
I like to use rsync, but the speed is so slow. Is there way to fix this?
Thanks,

---

