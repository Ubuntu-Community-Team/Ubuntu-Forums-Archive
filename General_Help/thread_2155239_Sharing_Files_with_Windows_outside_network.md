---
title: "Sharing Files with Windows outside network?"
date: 2013-06-17
forum: General Help
---

### Post by sslx on 2013-06-17
What's the best way to share files between Ubuntu and Windows that are outside of the network?
I tried Samba, but I couldn't get Ubuntu to accept connection from outside lan.
Is there way to allow Samba server to accept connection from outside?
Temporarily I'm using seafile that's kind of dropbox, but it's little slow.
I just wanted to see if there's another solution.
Thanks,

---

### Post by Cheesemill on 2013-06-17
> **sslx said:**
> Is there way to allow Samba server to accept connection from outside?

Yes it is possible, but don't do it because it is incredibly insecure.

The easiest way would be to install openssh-server on your machine and forward port 22 on your router then just connect either with the Ubuntu file manager or with WinSCP from a Windows machine.

---

### Post by sslx on 2013-06-17
I need to mount the sharing folder though.
An application needs to watch a folder to process when a new file gets added.

---

### Post by user_of_gnomes on 2013-06-17
Why not use an FTP server? [https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html) and [http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

---

### Post by Cheesemill on 2013-06-17
You can do that.

[http://superuser.com/questions/291786/map-ssh-drive-in-windows](http://superuser.com/questions/291786/map-ssh-drive-in-windows)

---

### Post by HiImTye on 2013-06-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you can use SSH to forward Samba, although the process is a little involved on Windows.
[http://www.blisstonia.com/eolson/notes/smboverssh.php](http://www.blisstonia.com/eolson/notes/smboverssh.php)
or you can set up a VPN over SSH, also a little involved, but it has the advantage of bringing the rest of the network with it
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)
[https://wiki.archlinux.org/index.php/VPN_over_SSH](https://wiki.archlinux.org/index.php/VPN_over_SSH)
[http://bodhizazen.net/Tutorials/VPN-Over-SSH](http://bodhizazen.net/Tutorials/VPN-Over-SSH)

---

### Post by sslx on 2013-06-18
Thanks for the suggestions! Sftp drive sounds good.

---

