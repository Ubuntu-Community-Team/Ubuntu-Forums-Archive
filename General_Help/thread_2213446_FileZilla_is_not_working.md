---
title: "FileZilla is not working"
date: 2014-03-26
forum: General Help
---

### Post by emptycoder on 2014-03-26
FileZilla was working great but now for some unknown reasons it doesn't work anymore, I tried to upload some files to my website but I  couldn't connect to FTP server and start getting Connection Timed Out error, even  increasing the timeout is not helping. I contacted Host provider  and they told me everything is working fine, I tried to access the  server with web based FTP client and it worked!? I tried to access with  VPN connection and it did work too.
I don't understand what's the problem?
Please help me, thanks.

---

### Post by Habitual on 2014-03-28
try it from c-line using terminal>
```
ftp user@example.com
``` or ```
ftp > open example.com
```

or maybe use the IP instead of "name"?

---

### Post by Lars Noodén on 2014-03-29
It's also possible they turned it off and have [stopped using FTP](https://www.google.com/search?q=stop+using+ftp).  FileZilla supports SFTP, which is a different (and secure) protocol.  See if you can connect with SFTP on FIleZilla.  If you can connect, consider changing your password, too.

---

### Post by emptycoder on 2014-04-03
Sorry for late replay, the problem was solved, it was DNS who causing that so that's why FileZilla works with VPN.
I was using Comodo DNS and I change it to Google Public DNS.
Removing DNS or using another DNS was the solution

---

