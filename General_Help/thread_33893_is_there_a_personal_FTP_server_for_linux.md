---
title: "is there a personal FTP server for linux"
date: 2005-05-12
forum: General Help
---

### Post by ianbillmorris on 2005-05-12
Hi,

I am after a personal ftp server ie something I can run as a user from the desktop that 
will allow me to recieve files via ftp without running a fully fledged ftp server.

It would need to support NAT as I am behind a router (but can forward ports)

I found almost exactly the thing but it is for windows rather than linux

[http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/)

Anyone come across anything like this for linux?

Cheers

Bill

---

### Post by jdodson on 2005-05-12
gftp.  it is available in universe.

---

### Post by ianbillmorris on 2005-05-13
Not really what I was after.  I want an FTP server not a client but not the normal unix style deamon running the background type thing.

I am not even sure if the app I want actually exists. It is a fairly ovbious idea so I am surprised that no-one has come up with it before.

If not it may give me the reason I have been looking for to actually learn somthing more usefull then VB and write the thing myself.

Basically what I want is an application that as a normal non-root user I can start within X Window that will start an FTP server on my PC.  I want to be able to give a url, username and password to say a non-techical windows user to put into windows explorer and have him upload or download a file onto my PC via FTP.  When I close the app down I want the ftp service to stop again.

I know I could setup an ftp deamon to run in the background but that is overkill for my needs

If anyone has any ideas please let me know.

Cheers

Bill

---

