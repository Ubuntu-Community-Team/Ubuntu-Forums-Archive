---
title: "FTP multiple file upload problem"
date: 2013-07-02
forum: General Help
---

### Post by mickey13 on 2013-07-02
I am having a problem uploading multiple files to my vsftpd server.  It seems to me like the data connection is getting shutdown before the transfer finishes.

Notes:
[LIST]
[*]vsftpd version 3.0.2 as my FTP server
[*]connect via ftpes
[*]user is a virtual user (not system user)
[*]works fine on LAN
[*]problem happens with multiple clients (BitKinex, FileZilla, lftp)
[/LIST]

I realize the "works fine on LAN" note above indicates firewall or router issue, but for testing, I've disabled the firewall on my Ubuntu server, on my router, and my cable modem.  Plus I can login in, and transfer files sometimes (usually only one file at a time, and that file doesn't already exist on the remote file system (the problem still happens when I upload multiple files with none of them already existing on the remote file system)).

Thoughts?

Here's a log snippet from my vsftpd server:
```
FTP response: Client "<snip>", "331 Please specify the password."
DEBUG: Client "<snip>", "SSL version: TLSv1/SSLv3, SSL cipher: AES128-SHA, not reused, no cert"
FTP command: Client "<snip>", "PASS <password>"
OK LOGIN: Client "<snip>"
FTP response: Client "<snip>", "230 Login successful."
DEBUG: Client "<snip>", "SSL shutdown state is: SSL_RECEIVED_SHUTDOWN"
DEBUG: Client "<snip>", "SSL shutdown state is: 3"
FTP command: Client "<snip>", "OPTS UTF8 ON"
FTP response: Client "<snip>", "200 Always in UTF8 mode."
FTP command: Client "<snip>", "PBSZ 0"
FTP response: Client "<snip>", "200 PBSZ set to 0."
FTP command: Client "<snip>", "PROT P"
FTP response: Client "<snip>", "200 PROT now Private."
FTP command: Client "<snip>", "CWD /"
FTP response: Client "<snip>", "250 Directory successfully changed."
FTP command: Client "<snip>", "TYPE A"
FTP response: Client "<snip>", "200 Switching to ASCII mode."
FTP command: Client "<snip>", "PASV"
FTP response: Client "<snip>", "227 Entering Passive Mode (<snip>)."
FTP command: Client "<snip>", "STOR test1"
FTP response: Client "<snip>", "150 Ok to send data."
DEBUG: Client "<snip>", "SSL version: TLSv1/SSLv3, SSL cipher: AES128-SHA, not reused, no cert"
DEBUG: Client "<snip>", "SSL shutdown state is: SSL_RECEIVED_SHUTDOWN"
DEBUG: Client "<snip>", "SSL shutdown state is: 3"
OK UPLOAD: Client "<snip>", "/test1", 0.00Kbyte/sec
FTP response: Client "<snip>", "226 Transfer complete."
FTP command: Client "<snip>", "PASV"
FTP response: Client "<snip>", "227 Entering Passive Mode (<snip>)."
FTP command: Client "<snip>", "STOR test2"
FTP response: Client "<snip>", "150 Ok to send data."
DEBUG: Client "<snip>", "SSL version: TLSv1/SSLv3, SSL cipher: AES128-SHA, not reused, no cert"
DEBUG: Client "<snip>", "SSL shutdown state is: SSL_RECEIVED_SHUTDOWN"
DEBUG: Client "<snip>", "SSL shutdown state is: 3"
OK UPLOAD: Client "<snip>", "/test2", 0.00Kbyte/sec
FTP response: Client "<snip>", "226 Transfer complete."
FTP command: Client "<snip>", "TYPE I"
FTP response: Client "<snip>", "200 Switching to Binary mode."
FTP command: Client "<snip>", "PASV"
FTP response: Client "<snip>", "227 Entering Passive Mode (<snip>)."
FTP command: Client "<snip>", "LIST"
FTP response: Client "<snip>", "150 Here comes the directory listing."
DEBUG: Client "<snip>", "SSL version: TLSv1/SSLv3, SSL cipher: AES128-SHA, not reused, no cert"
DEBUG: Client "<snip>", "SSL shutdown state is: NONE"
DEBUG: Client "<snip>", "SSL shutdown state is: SSL_SENT_SHUTDOWN"
DEBUG: Client "<snip>", "SSL shutdown state is: 3"

```

---

### Post by mickey13 on 2013-07-02
I've actually been looking for a solution to this for a while now.  I actually think I'm going to give up on vsftpd.  Does anyone have a recommendation for another ftp server (and a quick reason why you'd recommend it)?  Thanks.

---

