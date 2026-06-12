---
title: "Update"
date: 2007-02-16
forum: General Help
---

### Post by Ambimom on 2007-02-16
Does anyone understand why this appeared all of a sudden?  Can I fix it? 

[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)

---

### Post by aysiu on 2007-02-16
Does this help?
[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

---

### Post by Ambimom on 2007-02-17
I'm not behind a proxy.  I am connected directly to the Internet.  

But this morning, the error message changed. > [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Sub-process gzip returned an error code (1)

Apparently this repository was updated on February 15, which might explain why I never encountered the problem until yesterday.  I also found this post from February 3, 2007: 
> It looks like all of a sudden, within the last week, lots of people get this error. I'd say the issue is with the repository, or repositories, cause they seem to different.
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [22.5kB] 
99% [5 Sources gzip 0] 20.9kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources 
Sub-process gzip returned an error code (1)
Fetched 5B in 6s (1B/s) 
Reading package lists... Done

Any ideas?

---

### Post by bapoumba on 2007-02-17
Hello Ambimom :)

I see these error coming quite frequently to the forums. The closest explanation I found as to why ftp will work better than http in sources.list is in that thread:
[http://www.ubuntuforums.org/showthread.php?t=9944]("http://www.ubuntuforums.org/showthread.php?t=9944")

Sometimes, this will work:
```
sudo aptitude clean
sudo aptitude update
```
without changing the mirrors in sources.list file, or switching to ftp.

Cheers.

---

### Post by Ambimom on 2007-02-17
Thanks for the help.  I tried your suggestions....close but it did not work, but it did give me an idea to try....

I opened Synaptic /Settings / Repositories 

I highlighted each of the Security Updates, clicked on edit, and changed the http to ftp manually.  

That worked!

I reloaded, and the gzip error message was gone!

Another problem solved!:lolflag:

---

