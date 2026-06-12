---
title: "apt cannot established connection to the server"
date: 2006-11-12
forum: General Help
---

### Post by antid0te on 2006-11-12
hello all..:KS 

I have serious problems here, my laptop is installed edgy and after i upgrade some applications like...

samba, vsftpd, apache, wine, thunderbird, xchat, bluetooth, mysql, shorewall, hdparm, lmsensors, nessusd, xinetd, inetd, etc...

third party software are:
webmin, vnc2swf, wink...

it opened so many ports, and after a few minutes..the apt-get cannot establish a connection to the server..

the error log said like this::-# 

t0m@antitrust:~$ sudo apt-get update
Password:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
:mad: :mad: :mad:  (i don't understand !!)

Internet connection is established well, as i post this message..
What happened with apt ?i don't wanna reinstall it..](*,)

---

