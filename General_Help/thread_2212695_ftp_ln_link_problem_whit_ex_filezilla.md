---
title: "ftp ln link problem whit ex filezilla"
date: 2014-03-22
forum: General Help
---

### Post by phs2004 on 2014-03-22
Hi, Im trying to link a dir from /media/ to /home/anders but ln dont show in ex filezilla. Works fine in ssh client like putty. Or in terminal. Im using Ubuntu 12.04 server. 

ln -s /media/movies_hd/ /home/anders/movies_hd

Tryed this to chown -R anders:anders /media/500GB 
and
chmod -R 777 /media/movies_hd

I have no clue why it dosent work. I have seen links in ftp programs before.

Can i mount one harddrive serveral times? :D Havent tryed that, dont think that works.

---

### Post by TheFu on 2014-03-22
What file system is hte external drive formatted using? 
I'd use
[code]ln -s /media/movies_hd /home/anders/[/code
]as the symlink command.

FTP is bad and should be avoided unless there isn't any other choice AND security doesn't matter. There are sftp solutions for every platform.  I haven't used FTP in about 15 yrs.

---

### Post by phs2004 on 2014-03-23
They are all xfs filesystem. So if not ftp how then can i let my frends download from me?

edit: Ok changed my proftpd to SSL/TLS. Tested and works whit filezilla.

Guess I have to go and grab an old harddrive mount in /etc/fstab to /home/anders/movies_hd  and copy over files haha :P

---

### Post by TheFu on 2014-03-23
[https://www.google.com/search?client=ubuntu&channel=fs&q=stop+using+ftp&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=stop+using+ftp&ie=utf-8&oe=utf-8)

If you want to share with the world, use HTTP or BT. Much easier for firewalls.
If you want to share with friends, setup **sftp**.  FTPS just feels - wrong - but might be fine. I dunno.

Every major FTP server has had back-door code discovered in the last few years. Sometimes that code wasn't discovered for over a year.

---

### Post by phs2004 on 2014-03-23
Ok going to change it to sftp efter my kid going to sleep. The setup i did this morning was ftps whit implicit over tls.  But the main question still dont work :D how to ln -s my folders :D

---

### Post by TheFu on 2014-03-23
It isn't an issue here with CLI sftp from Linux - just tested it.  Also worked using pcmanfm (a Linux file manager). Seems like an issue with filezilla not understanding symlinks.  I don't recall winscp having this problem - but don't really use Windows that much to know. Sorry.  I spend most of my time on Linux.

In any Linux file manager, just put sftp://server/directory/ into the path. If the client and server have ssh-keys already, the connection is made automatically. I suspect if there are not keys (don't ahve any servers like that here), then ssh credentials will be requested.

[https://serverfault.com/questions/448647/symbolic-link-and-filezilla-over-sftp](https://serverfault.com/questions/448647/symbolic-link-and-filezilla-over-sftp) seems related and has the mount --bind option.

---

### Post by phs2004 on 2014-03-23
Ok, Thanks going to test all this later on. Will post when I get it all working.

---

### Post by TheFu on 2014-03-23
> **phs2004 said:**
> Ok, Thanks going to test all this later on. Will post when I get it all working.

Booted Windows7 - WinSCP works with the symlinks over SFTP here.  Don't know why filezilla shouldn't work the same unless the SFTP environment is chroot'd.

---

### Post by phs2004 on 2014-03-24
Ok got it all working. I removed proftpd and installed vsftpd configure it to sftp. Testet the symlink and it worked in both WinSCP and Filezilla :D 

sftp://anders@192.168.1.100:2222 :D and a nice icon whit movies_hd and a nice arrow :D Tanks now its both secure and working.

---

### Post by TheFu on 2014-03-24
sftp is built-into the ssh server we already run. It gets carefully reviewed, since it is the cornerstone for most UNIX administrators. It has amazing security features, is well understood, and documented. Why not use it?

These are from a few yrs ago about the 2 programs you've mentioned:
* [http://thehackernews.com/2011/07/video-demonstration-vsftpd-backdoor.html](http://thehackernews.com/2011/07/video-demonstration-vsftpd-backdoor.html)
* [http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787](http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787)
So - I don't think these programs are anywhere near as secure as openssh-server is.
Also, be certain to [secure the ssh/scp/sftp connections.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")

Of course, I could find a link about ssh on Ubuntu as well ... though I didn't see any relevant links on the 1st pg of results.

---

### Post by phs2004 on 2014-03-24
My vsftpd setup uses same keys as in /etc/ssh and uses same ports as ssh login via ssh client. I need some type of (s)ftp access to my server.
 I host a a few websites for friends. Vsftpd and Proftpd are the most used ftp servers. I dont know any other way to set this up.

---

### Post by TheFu on 2014-03-24
Clearly, it is up to you.

There is no need for any FTP servers. Use the built-in sftp server that is already running as part of the openssh-server on the box. You can limit where certain users have access and only allow sftp, preventing scp, ssh use at the userid level.

[http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze](http://www.howtoforge.com/restricting-users-to-sftp-plus-setting-up-chrooted-ssh-sftp-debian-squeeze)

openssh-server configuration is proven, well-known, secure.

---

### Post by phs2004 on 2014-03-24
Hmm, thats instresting. You meen like that. Dident know that at all. Did not know you could run ssh whit sftp. Just thought you had it to putty client. 

Going to test ofcourse :) And it works whit standard ftp clients like filezilla and winscp?

---

### Post by TheFu on 2014-03-24
> **phs2004 said:**
> Hmm, thats instresting. You meen like that. Dident know that at all. Did not know you could run ssh whit sftp. Just thought you had it to putty client. 

Going to test ofcourse :) And it works whit standard ftp clients like filezilla and winscp?

I had NEVER considered loading an FTP server when sftp was built-into the ssh-server already. ;)
There are parts of the FTPS protocol that I find concerning. The ability for a client program to reject the security is troubling. Clients shouldn't get to choose what the security level used is, IMHO, especially if passwords are being transmitted.

---

### Post by phs2004 on 2014-03-24
Hmm think I need to test this first on a Virutal server.

---

### Post by phs2004 on 2014-03-25
Ok got it all working but used a lite easier way to lock user in home dir.

chown root:root /home/anders
chmod 755 /home/anders


and in sshd-config

Subsystem sftp internal-sftp

Match User anders
    ChrootDirectory /home/anders/
    AllowTCPForwarding no
    X11Forwarding no
    ForceCommand internal-sftp

And removed all ftp servers only using openssh. Now then, this must be ok or?

Edit: Symlinks works to of course hehe :P 
Edit2: Symlinks dident work. But added "/media/movies_hd /home/anders/movies_hd auto bind" to fstab, then it works great :)

---

