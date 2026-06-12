---
title: "how to ftp to a ubuntu box"
date: 2008-02-04
forum: General Help
---

### Post by markp1989 on 2008-02-04
I have a spare machine i would like to set up as a torrent slave, i have ubuntu installed, and Deluge for downloading, deluge is set to auto download any torrents in my home folder, 

i would like to be able to log in to this computer from my other computers using gftp, so i could drop torrent files on the drive, and copy downloaded files to other  computers.


how do i go about setting this computer up so that it can be connected to by other computers with read right support?

any help will be highly appriciated

---

### Post by taurus on 2008-02-04
You need to install an ftp server on your Ubuntu machine so you can ftp to it, downloading and uploading stuff.  You can use either vsftpd or proftpd (and a few others that you can choose).  I use vsftpd on all my Linux machines.

---

