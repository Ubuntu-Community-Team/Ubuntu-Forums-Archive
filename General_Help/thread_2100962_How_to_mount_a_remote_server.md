---
title: "How to mount a remote server"
date: 2013-01-03
forum: General Help
---

### Post by LiorAmitai on 2013-01-03
Hello,

Is ther any way to mount a directory on a remote server using ubunto 12.10?

Thanks.

lior

---

### Post by conradin on 2013-01-03
curlftpfs, [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)
Theres actualy alot of ways. What are you trying to do?
are you loging in via a remote protocol, or accessing web based folders?
What are you trying to do after mounting?

---

### Post by btindie on 2013-01-03
As the previous poster said there are various forms of networked filesystems, it just depends on what you want to do. They include

NFS - native networking filesystem for Linux
CIFS - uses Samaba to provide windows networking support
WebDAV - uses a web server, i.e. Apache
FTP - pretty common
SSH/SSHFS - easiest way to move files about, can also mount via SSHFS

---

### Post by LiorAmitai on 2013-01-03
Hi,

Thanks for the reply.
I'm trying to access a remote server to gain alow me to install an application from it.

---

### Post by conradin on 2013-01-03
do you need login credentials or can you down load the file directly with something like wget? Do you know the path of the remote files you need?
wget is probably the best program in all of linux for getting files from servers, but without more info its hard to say how to use it. 

can you be more specific?

heres an example of downloading a file, where I know the path to the download, using wget:
```
wget 130.111.192.241/fcc_10.014_all.deb

```

---

### Post by LiorAmitai on 2013-01-03
Hi,

Iknow the path on the server.
The issue is i want to mount the driver since it requires domain\Username & Password.

Once I will be able to mount the driver on the remote server i wil be able to go to the installation path and install the application on my VBox.

---

### Post by tgalati4 on 2013-01-03
Make a local directory: (Open a terminal)

```


cd
mkdir MyRemoteServerDirectory
sudo mount Server:/Home/YourUserName/DirectoryofInterest MyRemoteServerDirectory
cd MyRemoteServerDirectory

```

---

