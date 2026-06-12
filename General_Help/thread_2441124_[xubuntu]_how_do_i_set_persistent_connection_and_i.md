---
title: "[xubuntu] how do i set persistent connection and infinite timeout in FTP cmd line ..."
date: 2020-04-19
forum: General Help
---

### Post by dbee on 2020-04-19
I'm connecting to my remote shared hosting server and i keep timing out. I'm using the command line FTP in emacs.

I believe i can set 'hash' to stop file transfers from timing out, but i'm not transferring any files.

I need a general infinite ( or as long as possible ) timeout setting. This is probably a remote server issue though right ? Seeing as how i don't have command line access (it's a shared server) I guess i'm out of luck no ?

What about automatic login ? That surely is a local system setting. Where and how i store my login details ?

Thanks,

---

### Post by TheFu on 2020-04-19
Plain FTP shouldn't be used since ... 2002, maybe 2006.  sftp, ssh, scp, rsync are the more secure methods that should be used.  If the provider doesn't support those, they should have been fired 14 yrs ago.

[https://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](https://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

.netrc might be the answer you seek, but the better answer is to setup sftp and use ssh-keys for authentication.

---

### Post by HermanAB on 2020-04-21
Ayup - FTP is only good on a small LAN, not on a WAN.

An exception is when you configure a FTP server with split upload and download directories and don't allow any of the control commands, which the OP need to use.

In the case of the OP, I would suggest finding a new data centre, e.g. Linode.

---

### Post by dbee on 2020-05-01
Relax, it's ftp over TLS. It's encrypted.

Host doesn't have SSH for obvious reasons I suppose. 

FTP will have to do. 

Still don't know how to open persistent connections though :-(

---

