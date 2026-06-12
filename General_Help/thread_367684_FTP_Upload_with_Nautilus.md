---
title: "FTP Upload with Nautilus"
date: 2007-02-22
forum: General Help
---

### Post by showcaser on 2007-02-22
Hello,

I am trying to upload files from my home (Ubuntu 6.10) computer to a server I have setup at my university (windows XP, Cerberus FTP server) using Nautilus. I have used the "Connect to server" or just entered it in as a location and while I can browse and download files I can't seem to upload (using copy-> paste or drag and drop).

The ftp server logs the transfer as a "Failed Download" and I noticed the log says Nautilus is applying a RETR command instead of a STOR command on the file.

I'm pretty sure it's not a server issue as upload/downloads and all work fine with gFTP. I really like, though, the convenience of using Nautilus to browse and transfer.

Thanks for any suggestions!

---

### Post by z987k on 2007-02-22
try GFTP instead.  If it's not pre-installed it's in the repositories.

---

### Post by showcaser on 2007-02-22
Thank you for the reply.

As mentioned it works fine with gFTP, and a couple other programs I have tried.

I've reviewed the server log and it appears that Nautilus (when an upload of a file is initiated) first switches to the directory where the file is to be stored. Then it tries to change to a directory named after the file (? :confused: ? then it initiates the RETR command on the file, even though it should be trying to STOR the file.

Perhaps a bug with Nautilus?

---

