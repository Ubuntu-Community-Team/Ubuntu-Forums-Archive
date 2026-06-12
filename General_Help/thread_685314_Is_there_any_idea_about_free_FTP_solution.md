---
title: "Is there any idea about free FTP solution?"
date: 2008-02-02
forum: General Help
---

### Post by eric12 on 2008-02-02
I am a newbie and desire to know more and more about Free FTP solution and its providers. I am working in a software company and I am in the need of high quality and most efficient SFTP?

---

### Post by musther on 2008-02-02
Do you want an FTP client or server.  If you need an FTP client (to connect to an FTP server), then I would recommend FileZilla, it's cross platform and in the ubuntu repositories:
[http://filezilla-project.org/](http://filezilla-project.org/)

If you need an FTP server, that's a different kettle of fish, but there are some in the repos.
You mentioned SFTP (which is really file transfer over an SSH connection), you can use FileZilla for a client, and if you want to set up a server on Ubuntu, simply install the SSH server:
```
sudo apt-get install openssh-server
```

Hope that helps

---

### Post by steve_waters on 2008-02-02
Another good client is gFTP again in the repos

---

### Post by nemilar on 2008-02-02
gFTP seems to be the most common ftp/sftp client.

You may want to lake a look at SSHFS, though:

[Link: How to mount a drive over a network/internet via sshfs (http://www.techthrob.com/tech/sshfshowto.php)]("http://www.techthrob.com/tech/sshfshowto.php")

---

