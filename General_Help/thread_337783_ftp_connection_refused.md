---
title: "ftp connection refused"
date: 2007-01-13
forum: General Help
---

### Post by chocolatetoothpaste on 2007-01-13
Hey all,
I am sorry if this has been answered, but I couldn't find it.  This is the situation.  I have setup a webserver in my office.  it just serves pages for the developers so we all work on the same version of the site.  I am trying to connect to the server with an ftp program to upload and download files, both on the intranet, and remotely through the internet.  Every time I try to connect, it says connection refused.  I got ssh to work by installing openssh (or something), but I can't connect with an ftp client on windows.  What do I need to do to allow connections?

---

### Post by taurus on 2007-01-13
You need to install the server of ssh, sshd.  Or you have to install a ftp server like vsftpd, proftpd, etc.

---

### Post by chocolatetoothpaste on 2007-01-13
Okay, I installed proftpd and it worked.  I apologize for not trying it sooner.  I didn't understand what it was.  Here is a follow-up question, is there any way I can set a default directory to connect to when users from a certain group connect?

---

### Post by taurus on 2007-01-13
Also install the gproftpd (GUI for proftpd) and use it to configure your proftpd.

```
sudo aptitude install gproftpd
```

---

