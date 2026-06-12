---
title: "FTP to web documents directory"
date: 2020-01-17
forum: General Help
---

### Post by cearlp2 on 2020-01-17
How do you ftp to /var/www/html on an ubuntu 18.04 system?
When I use /var/www/html/... as the remote filename I get a /var/www/html/... in the users home directory.
I can't change out of the users home directory before doing the put.

---

### Post by TheFu on 2020-01-18
use sftp, not the insecure plain FTP.

---

### Post by cearlp2 on 2020-01-18
And if sftp is not a choice?

---

### Post by Morbius1 on 2020-01-18
Because you chroot'ed your ftp users and created a symlink from outside your home directory to your home directory?

You might consider a bind mount instead of a symlink.

Note: I don't remember how long it's been since I did ftp but I think this will work. I offer this as an example:

I have a directory ( /Test ) on my ftp server.
I added a file to that directory ( test.txt )
I created a symlink from /Test to /home/tester
I connected to the vsftpd server and did an ls against /Test:
> ftp> ls Test
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
226 Directory send OK.

Now on the server I created a new folder in my home directory ( Test2 ).
I then did a bind mount from /Test to /home/tester/Test2:
```
sudo mount --bind /Test /home/tester/Test2
```
If I now do an ls against Test2 I will get the contents of /Test:
> ftp> ls Test2
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
-rw-r--r--    1 0        0               0 Jan 18 10:41 test.txt
226 Directory send OK.
ftp> 

---

### Post by TheFu on 2020-01-18
> **cearlp2 said:**
> And if sftp is not a choice?

I'd fire that webhost and move to be better provider.  Security failures like requiring the use of non-secure protocols have no excuse today.

---

### Post by SeijiSensei on 2020-01-18
If you control the system, you can implement SFTP by installing openssh-server. You can then use SSH for remote access as well.

---

### Post by cearlp2 on 2020-01-18
I failed to mention that the web host I'm talking about is on my LAN and is accessed only by me from another machine on that LAN.

---

### Post by TheFu on 2020-01-18
> **cearlp2 said:**
> I failed to mention that the web host I'm talking about is on my LAN and is accessed only by me from another machine on that LAN.

There are so many better tools for deploying files than plain FTP.  **rsync** is how I do it.  That works over **ssh** by default.  ssh is how  Unix systems are connected, managed, maintained world-wide.  Plain FTP should have died off in 2000.

---

### Post by gsahli on 2020-01-18
open-ssh on the server (this is standard install on Ubuntu) and Filezilla for a gui app on the sending client

---

### Post by SeijiSensei on 2020-01-19
Openssh-server is not part of the standard installation for the desktop. It's included in Ubuntu Server. On a desktop you need to run "sudo apt install openssh-server".

---

### Post by HermanAB on 2020-01-19
I agree that ssh is the way to go in a pure Linux environment.  However, if you are on a small LAN and also have to serve Windows machines, then Anonymous FTP is still a good option.  (Note that the latest Windows 10 now has limited support for SSH built in).

FTP is light weight.  The design of FTP is such that the client does most of the work.  It is natively supported by all versions of Windows and you can map a server share in the file browser with little ado.  Anonymous FTP is completely public, doesn't use passwords and doesn't expose your security credentials.

---

### Post by cearlp2 on 2020-01-20
All the answers are probably valid in most cases but not in mine.
A software program I am using on one machine wants to ftp its result to another machine on my LAN.
The results need to be placed in the /var/ww/html directory.
I created a symlink in my home directory to the /var/www/html directory but the results go into an html directory in my home directory not the /var/www/html directory.
I solved my problem by making the /var/www/html directory writeable by everyone to get the ftp to write to it than changed it back to it's original permissions.

---

### Post by cearlp2 on 2020-01-21
Thanks for all the suggestions.

---

### Post by TheFu on 2020-01-21
In the early 2000s, we had programs that insisted on using plain FTP.  sftp has an interface that is exactly the same. This is deliberate.  What we did was to copy the sftp program into the plain FTP program and the calling program just worked ... using sftp ... without any complaints.

---

