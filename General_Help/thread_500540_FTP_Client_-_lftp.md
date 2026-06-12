---
title: "FTP Client - lftp?"
date: 2007-07-14
forum: General Help
---

### Post by EdUbun on 2007-07-14
Hi all,

I messing around with ftp clients for uploading website folders. I tried filezilla, fireftp, and gftp. They all realy don't seem to satisfy the needs. I want a simple fast ftp client. Perferable with option chmod (like gftp) and a synchronize option so I don't need to keep selecting the files which are altered. This last one is what I can't find, it's in fireftp but I don't want it plugged in, I also like to be able to schedule ftp for backups.

Any ideas about lftp?

---

### Post by marsbt on 2007-07-14
one that comes to mind is ncftp2 but I haven't used it in a long long time. If you have a choice you should use SSL encryption for your ftp transfers for security.

---

### Post by HermanAB on 2007-07-14
Maybe look into rsync over SSH.

Cheers,

Herman

---

### Post by EdUbun on 2007-07-17
If i go to use rsync, can you enter exceptions? There are three file (config files) with on the host are different and shouldn't be overwritten.

---

### Post by EdUbun on 2007-07-18
Well I found weex. This is do together with lftp.
Only need to schedule it maybe.

---

