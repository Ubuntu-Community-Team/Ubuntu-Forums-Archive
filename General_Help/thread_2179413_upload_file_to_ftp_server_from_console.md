---
title: "upload file to ftp server from console"
date: 2013-10-08
forum: General Help
---

### Post by Marchello_Lippi on 2013-10-08
Hi all, 

how do I upload file to ftp server from console?

---

### Post by Lars Noodén on 2013-10-08
Hopefully upload for [FTP has been turned off](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  "Anonymous FTP" is ok for downloads.  That is read-only, but uploading requires a login and would be very insecure using FTP.  That said, there is a secure method for upload called [sftp](http://manpages.ubuntu.com/manpages/raring/en/man1/sftp.1.html) and hopefully that is what you have available.  You can run it from the console or terminal something like this:

```

sftp marchello_lippi@someserver.example.org

```

Be sure to read the manual page for [sftp](http://manpages.ubuntu.com/manpages/raring/en/man1/sftp.1.html) so that you can see which commands the program has available to you for file transfer.  Look in the manual page for "put" and "get"

---

