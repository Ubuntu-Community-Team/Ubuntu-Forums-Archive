---
title: "Cant Access FTP (proftpd)"
date: 2013-01-12
forum: General Help
---

### Post by jgraham95 on 2013-01-12
Having a bit of an issue.

I recently installed Proftpd with gadmin-proftpd and default configuration, but when i try and access the ftp via a user account I get past the username screen but once the password is inputted the system hangs.

I see this in my clients log

```
[R] Connected to xxxxxxxxxxx
[R] 220 My FTP Server
[R] USER xxxx
[R] 331 Password required for xxxx
[R] PASS (hidden)

**Logging in
```

I've also set the account to not require a password to see if i can gain access and I get the same issue.

The only way i can seem to connect is via a web browser. however this also hangs when i put in credentials but does eventually connect. however if i want to access a file it times out.

Any suggestions on ways I could resolve this issue?

Any help is greatly apreciated

---

### Post by 2F4U on 2013-01-12
From the information you provide it looks to me as if the problem is on the side of the remote machine you are trying to connect. Maybe the machine is overloaded. Is there any chance to contact the admin of that machine?

---

