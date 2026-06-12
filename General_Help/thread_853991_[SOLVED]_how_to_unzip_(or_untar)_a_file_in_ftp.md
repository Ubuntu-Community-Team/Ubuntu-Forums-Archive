---
title: "[SOLVED] how to unzip (or untar) a file in ftp?"
date: 2008-07-09
forum: General Help
---

### Post by myidbe on 2008-07-09
Hi forum,

I was wondering if it is possible to unzip a zipped file (or tar -xvf for that matter) that is already uploaded to my ftp-space without downloading it. Eg, I have a zip file of a few photos, and it seems like it would be possible to extract it without downloading it, extracting, and re-uploading.

Specifically, is this possible from the command line ftp environment?

Any tips or pointers to related how-tos would be very much appreciated.

---

### Post by HalPomeranz on 2008-07-09
It's not possible inside of an FTP client.  If you had some other way to log into the remote system (say, via SSH), you could log into the remote machine and unpack the file with a command like "tar zxf somefile.tar.gz".

---

