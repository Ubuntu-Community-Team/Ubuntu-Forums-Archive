---
title: "ubuntu 12 FTP server, how to use orig file time"
date: 2012-12-02
forum: General Help
---

### Post by ctny on 2012-12-02
I am using SyncBack to backup files from my Win7 box to Ubuntu 12 server using regular FTP. 

(I set up vsftpd server using the guide here [https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html))

The problem is all the files end up with the file transfer timestamp on Ubuntu instead of the original timestamp on Win7. So for each backup, Syncback transfers all the files over again thinking the files are not the same instead of just the changed files.

Is there a way to use the original timestamp of the source files? If vsftpd can't do it, is there an FTP server that can?

---

### Post by Wim Sturkenboom on 2012-12-03
Although this information is old, it might still be applicable: [http://www.linuxquestions.org/questions/linux-server-73/vsftpd-keep-client-timestamp-on-uploaded-file-695831/](http://www.linuxquestions.org/questions/linux-server-73/vsftpd-keep-client-timestamp-on-uploaded-file-695831/)

You need to find a server that supports the MFMT command; I don't know which one does. You also need the client to support it, so check the documentation of the client.

I used vsftpd and winscp to test and it did not work. winscp has the option to preserve the timestamp. So I guess it's vsftpd

---

