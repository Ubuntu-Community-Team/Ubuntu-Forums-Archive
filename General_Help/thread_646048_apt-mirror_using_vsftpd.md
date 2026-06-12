---
title: "apt-mirror using vsftpd"
date: 2007-12-20
forum: General Help
---

### Post by bturrie on 2007-12-20
I have an apt-mirror setup and working via apache on an xubuntu feisty system. I'm trying to convert to ftp access with vsftpd. vsftpd is installed and running. I can see the directory from another system on my lan (using anonymous login). 

My ftpuser is fpt and the home directory for that user is /home/ftp. I created a symlink to /var/spool/apt-mirror in /home/ftp. on the server Then I modified my sources.list on my desktop to point there, but apt is unable to get access to the files. 

Then I noticed that if I access the ftp server via say konqueror using [ftp://server-ip:21/](ftp://server-ip:21/), I can see the /apt-mirror/ directory but can't drill down into it. perhaps i'm jailed in the /home/ftp/ directory, everyone has read access to the directory and I can drill down as another local user on the server with no problems.

Another possibility could be a problem in my sources.list

entries there look something like

deb [ftp://server-ip:21/apt-mirror/mirror/archive.ubuntu.com/ubuntu/](ftp://server-ip:21/apt-mirror/mirror/archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe

which looks okay to me but maybe not.

---

### Post by geraldm on 2007-12-20
vsftpd has had different types of use.  
Under 1 version I used, access was restricted to the /home/ftp and subordinate directories.
Under another, I could log in as an allowed user on the machine, and cd anywhere permissions allowed.
The vsftp.conf and vsftp manpage has details.

Gerald

---

### Post by bturrie on 2007-12-21
Thanks for the reply. I've looked through the documentation several times and can't figure out which parameters need to be changed in order to open up access. At least not so far.

---

### Post by bturrie on 2007-12-22
poking around, I noticed that my inetd.conf file is not a text file. that doesn't seem to match with the man pages. my other xubuntu system is the same. Is that a problem??

---

### Post by bturrie on 2007-12-22
it looks like at least part of my problem was that i needed to set

anon_world_readable_only=NO

I still can't follow the symlink to my apt-mirror files but at least I can get to files in my anonymous user's home directory.

---

