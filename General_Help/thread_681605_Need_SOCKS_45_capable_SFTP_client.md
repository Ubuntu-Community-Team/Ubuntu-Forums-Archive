---
title: "Need SOCKS 4/5 capable SFTP client"
date: 2008-01-29
forum: General Help
---

### Post by Contess on 2008-01-29
Hi there

I am in desperate need for a SOCKS capable FTP/SFTP client. All the ones I was able to install through the add/remove feature do not have this feature.

Is there such a thing available for Ubuntu 7.10 . Also, if you could give me some installation advice in this in case synaptic does not support this (I am a Linux / Ubunto novice )

Kind regards and thanks

---

### Post by ounas on 2008-01-29
I dont know if there is one for Ubuntu, but have you looked at theis post..
[http://ubuntuforums.org/showthread.php?t=654176&highlight=socks+ftp]("http://ubuntuforums.org/showthread.php?t=654176&highlight=socks+ftp")


:)

---

### Post by Contess on 2008-01-29
> **ounas said:**
> I dont know if there is one for Ubuntu, but have you looked at theis post..
[http://ubuntuforums.org/showthread.php?t=654176&highlight=socks+ftp]("http://ubuntuforums.org/showthread.php?t=654176&highlight=socks+ftp")


:)

Hi, thanks for the link,
looked at that thread, interesting, it could be a solution to tunnel it through the browser but it would be sooo much more convenient to use a ftp client. 
Appearantly, Filezilla 2.2.23 had this feature but 3.0.0 does not. I am searching for such an older version now, no problem with using a 2x version as long as it gets the job done.

Anyone else having mor info on this topic ?

---

### Post by Contess on 2008-01-29
Well, I have found an older version on sourceforg.org:

[http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149](http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149)

Downloaded :
FileZilla_2_2_32_dbg.zip
FileZilla_2_2_32.md5

..and I am stuck now. :confused: How can I install this thing ?

---

### Post by ounas on 2008-01-29
Hope youve some luck finding what you want.

Ounas from the far cold north
:guitar:

---

### Post by Contess on 2008-01-29
> **ounas said:**
> Hope youve some luck finding what you want.

Ounas from the far cold north
:guitar:


yes I found it , but I believe it is source code and I have never built anything from source. Can you advise ?

cheers

---

### Post by Contess on 2008-01-29
apparently, all versions before 3.0 are windows, so we'd have to run it through Wine.

Any opinions ??

---

### Post by Contess on 2008-01-31
RESOLVED:

1.
Installed FireZilla 2.2.32 into wine

2.
Configured FireZIlla to use a Proxy at 127.0.0.1  port 8888

3.
sudo ssh -D 8888  username_at_proxyserver@proxy_server_IP


Works great

---

