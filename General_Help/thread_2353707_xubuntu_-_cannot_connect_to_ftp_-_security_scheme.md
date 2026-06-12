---
title: "xubuntu - cannot connect to ftp - security scheme"
date: 2017-02-24
forum: General Help
---

### Post by members2 on 2017-02-24
Hi there
I have 2 machines. On the first one i have xubuntu 16.04 desktop. On the second i have ubuntu 16.04 server. Each of them is in the same network. I don't add any iptables rules. iptables -L don't show any on each.
On the first machine with xubuntu desktop i could connect to ftp server with any problem. On the second machine with ubuntu server i have messages after enter login:
 - 500 This security scheme is not implemented
 - 234 AUTH TLS OK
 - [SSL Cipher DHE-RSA-AES256-SHA]
 - 200 PBSZ=0
 - 200 Data protection level set to "private"
 - 331 User user OK. Password required

On the machine with xubunt destkop after enter login i have:
  - 331 User user OK. Password required

Ofcourse i connect to the same server with the same login name.
I check packages with ssl, openssl, rsa....but after installing whole of packages i still have this messages.
Could any halp me what i must configure to work this.

---

### Post by TheFu on 2017-02-24
Welcome to the forums.

Don't use plain FTP. Use sftp.  There are many reasons, including that you get sftp for free by having ssh working and we all need ssh anyway.

---

### Post by members2 on 2017-02-24
That not solve my problem. I know i could use sftp. But i want answer why i have this message from one machine and don't have from another

---

### Post by TheFu on 2017-02-24
I haven't used plain FTP in decades (over 2), but looking at the messages, it seems 1 is using plain FTP and the other is trying to use something else. Plain FTP doesn't have any encryption - nowhere in the protocol.
```
- 500 This security scheme is not implemented
``` followed by TLS stuff?

I suspect the answer will depend on the specific FTP server you are trying to use, which ports it wants and if you are trying to use SFTP or FTPS on it. Something about a key exchange isn't working.

BTW, some of the language in the 1st post isn't clear. Important words seem to be missing. 
> could connect to ftp server with any problem. Does that mean it works or not?

It isn't perfectly clear which is the client and which is the server to me. "server" is ambiguous - "ftp server" or "server hardware" or "Ubuntu Server" installed?  Both systems will need both a "FTP client" and "FTP server" you wish to use.

Exactly which FTP servers are you running on which specific machines? Have they been configured?  What happens if you try to **\ftp localhost**? works? Same or different error?  Please show the entire transaction, including the exact command used.

Using the same login name doesn't mean the same credientials are used. Normally, userids/passwords are system specific unless you've setup LDAP, NIS, NIS+ or some other external authentication method in PAM for both systems.

sftp is much easier.

---

### Post by members2 on 2017-02-27
Hi. Thanks for reply.
Machine 1 is my computer where is installed distribution xubuntu-destkop-16.04
Macine 2 is my computer where is installed distribution ubuntu-server-16.04

The ftp serwer which i want to connect it is in external server. I don't have any permission to configure it. The ftp-server is pure-ftp
Welcome to Pure-FTPd [privsep] [TLS]

I cannot connect to this server via sftp: sftp -p ftp.server.com - no reaction on port 21 on port 22 connectioin refused

When i connect to server from 2 macine and send dir command i got this message - i must ctrl+c because no reaction - when i press ctrl+c i got this:
227 entering Passive Mode (123.123.123.123,116,199)
ssl_getc: SSL_read returned -1 - error: 00000000: lib(0):func(0);reason(0)
421 Service not available, remote server has closed connection
receive aborted
waithig for remote to finish

Maybe this give somebody a clue how to fix it.

---

### Post by HermanAB on 2017-02-27
Well, that is not really a FTP server.  It is a FTPS server.

Note that SFTP and FTPS aren't the same thing either.

I have never used  FTPS, so I am not familiar with the specific problems that you should expect with it, but in general, FTP uses multiple ports, so it usually has problems with any kind of firewall and because of the S part, you need to have some sort of SSL authentication and encryption going, which could have version specific bugs.

So, where does that leave you - up the creek without a paddle?

What you should do is read the man pages and look for the debug parameters and enable them.  You should then get more clues.

[http://rpm.pbone.net/index.php3/stat/45/idpl/3382716/numer/1/nazwa/ftps](http://rpm.pbone.net/index.php3/stat/45/idpl/3382716/numer/1/nazwa/ftps)

So try something like this:
$ ftps -d user@server

and see what pops up.  Then copy and paste whatever error message you get into google and see if anyone else in world is sharing your pain.

---

### Post by TheFu on 2017-02-27
I think **filezilla** supports FTPS.  The main issue I have with that protocol is that the CLIENT, not the server, gets to decide whether encryption is used.
Try filezilla or look for another FTPS client to try.

Looks like ftps uses ports 990 and 989 by default.
```
$ egrep -i ftps /etc/services 
ftps-data       989/tcp                         # FTP over SSL (data)
ftps            990/tcp

``` Don't know if that helps or not. Can't hurt to be aware.

running ftps returned 
...
Command 'ftp' from package 'ftp-ssl' (universe)
...

So perhaps installing that package could load a CLI ftps client? I dunno. Don't have **any** use for FTPS myself.

---

### Post by members2 on 2017-02-28
Ok. I found reason. I have installed ftp and ftp-ssl packages on macine 2 where is ubuntu-server-16.04. On macine 1 i have only ftp package. When I install ftp-ssl on macine 1 have the same problem which is on machine 2. I uninstall ftp-ssl, and everything works fine. Why that package brake ftp or overwrite ftp plain?

---

### Post by HermanAB on 2017-02-28
It seems to me that the server FTPS doesn't work and if you use a client that cannot do FTPS at all, it falls back to plain old FTP which then works.

---

