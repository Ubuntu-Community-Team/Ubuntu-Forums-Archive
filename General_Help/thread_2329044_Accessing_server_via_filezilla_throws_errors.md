---
title: "Accessing server via filezilla throws errors"
date: 2016-06-27
forum: General Help
---

### Post by Pandee on 2016-06-27
I have the following error when connecting to the FTP via filezilla. How do i fix this?

```



Command:    PORT 192,168,1,201,206,102
Response:    500 Illegal PORT command.
Error:    Failed to retrieve directory listing
Status:    Retrieving directory listing of "/home"...
Command:    CWD /home
Response:    250 Directory successfully changed.
Command:    PWD
Response:    257 "/home"
Command:    PASV
Response:    550 Permission denied.
Command:    
Response:    500 Illegal PORT command.
Error:    Failed to retrieve directory listing
Status:    Retrieving directory listing of "/"...
Command:    CWD /
Response:    250 Directory successfully changed.
Command:    PWD
Response:    257 "/"
Command:    PASV
Response:    550 Permission denied.
Command:
Response:    500 Illegal PORT command.
Error:    Failed to retrieve directory listing




Error:    GnuTLS error -110 in gnutls_record_recv: The TLS connection was non-properly terminated.
Status:    Server did not properly shut down TLS connection
Error:    Could not read from socket: ECONNABORTED - Connection aborted
Error:    Disconnected from server


```

Thanks,

Pandee

---

### Post by QDR06VV9 on 2016-06-27
Here is what I have needed to do:

    1.Open Filezilla, go to Edit -> Settings
    2.Click on Connection -> FTP: Choose Active
    3.Click on Connection -> FTP -> Active Mode: Select "Ask your operating system for the external IP address"
    4.Click on Connection -> FTP -> Passive Mode: Choose Fall Back to Active Mode
    Press OK.

Try connecting to your FTP site once again. Dose it now work?

---

