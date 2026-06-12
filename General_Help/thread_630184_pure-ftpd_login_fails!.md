---
title: "pure-ftpd login fails!"
date: 2007-12-03
forum: General Help
---

### Post by I.You on 2007-12-03
Hi there,

I've installed and configured pure-ftpd.
and started it:

# pure-ftpd &

I tried to access to ftp server from ftp client:

# ftp xxx.xxx.xxx.xxx
Connected to xxx.xxx.xxx.xxx.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 08:32. Server port: 21.
220 You will be disconnected after 15 minutes of inactivity.
Name (192.168.11.58:you): 
331 User you OK. Password required
Password:

and then, I entered the password correctly - I'm sure! - but following error:

530 Login authentication failed
Login failed.

I've changed the password several times:

# pure-pw passwd you
# pure-pw mkdb

However, it failed at last.
Any idea?

---

