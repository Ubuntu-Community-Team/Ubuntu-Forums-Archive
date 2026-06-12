---
title: "proFTPd - some confusion about permissions"
date: 2005-05-02
forum: General Help
---

### Post by stardotstar on 2005-05-02
Hi all,

I am confused about setting up my proFTPd server.

I am using Ubuntu as my dev server for my Debian Sarge live server which I am currently building.

I have installed proFTPd on both systems and it is working.

However I am totally stumped about how to get the access I want setup.

I have used the same basic/default proftpd.conf on both systems and I can get anon access to both but only the Ubuntu server will allow me to log in as a user on the system - even though the user is the same on both systems.  

On the Ubuntu server I can log in as my user account and write to my home directory or the ftp incoming directory, but on the Deb server with the same conf file I always get denied when I try to log in as a user account.  

The ftpusers conf is the same on both.

Is this a group thing?  Where should I start looking.  I have been parsing the proFTPd example configurations but they don't get specific about enabling authenticated users.  It seems that this is the default behaviour - due to the deny-all flag that can be set.  However this is not in effect on the Deb server.

Any pointers would be most appreciated.

Will

---

