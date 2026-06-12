---
title: "proftpd ignoring log in attemtps"
date: 2007-05-22
forum: General Help
---

### Post by stevenjo57 on 2007-05-22
Installed 6.10 server. No Gui. I do have Webmin working on it.

Setting up a system to allow clients off site  to upload files into their own ch(rooted) home directory.

Followed procedures in the Edgy wiki to install ftp server. Then followed procedure to ch(root) users in their home directory.

Now when I use a client to log in, I get nothing. Seems to just time out. Here is what the client says:

------------

Welcome to Core FTP, release ver 1.3c, build 1447.6 (U) -- © 2003-2006
WinSock 2.0
Mem -- 2,095,540 KB, Virt -- 2,097,024 KB
Started on Tuesday May 22, 2007 at 10:27:AM
Connect socket #580 to 192.168.0.6, port 21...
Connect socket #720 to 192.168.0.6, port 21...
Can't establish connection --> 192.168.0.6:21 @ Tue May 22 10:28:23 2007   (0-5)

----------------

Do I have to open a port? I saw nothing in the procedure about this. Does 6.10 server even include a firewall?

---

