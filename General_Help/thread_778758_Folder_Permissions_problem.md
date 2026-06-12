---
title: "Folder Permissions problem"
date: 2008-05-02
forum: General Help
---

### Post by rojmab on 2008-05-02
Hi,

I'm trying to accomplish the following:

Enable write access to /var/www/vpn by PHP
Enable write access to /var/www by the FTPusers group. It's only one user currently (Myself), with no plans for additional.

Currently /var/www is owned by root, belongs to group root.
Running Apache on Gutsy Gibbon.

I'm rather new to Linux... Can someone please help? Thanks!

---

### Post by drjesusphd on 2008-05-02
Look into the chmod command. That's what changes the read/write/execute permissions of your users and directories.

---

### Post by chunchengch on 2008-05-02
$ sudo chown yourloginname:yourloginname /var/www

---

### Post by rojmab on 2008-05-02
Hi, I have tried this:

```
ryan@ryan-desktop:/var/www$ cd ..
ryan@ryan-desktop:/var$ sudo chown ryan www
[sudo] password for ryan:

```

ls -al reveals:
```
drwxr-xr-x  4 ryan root  4096 2008-05-02 08:47 www
```


However, when I ftp to the box, and try to put a file into the www directory, I get permission denied...

```
C:\LocalData\Configs>ftp 10.4.18.100
Connected to 10.4.18.100.
220 Welcome to Ryan's FTP
User (10.4.18.100:(none)): ryan
331 Please specify the password.
Password:
230 Login successful.
ftp> cd /var/www
250 Directory successfully changed.
ftp> put testFile.txt
200 PORT command successful. Consider using PASV.
550 Permission denied.
ftp>

```

Any thoughts? Thanks.

---

### Post by warp99 on 2008-05-02
> **rojmab said:**
> Hi,

I'm trying to accomplish the following:

Enable write access to /var/www/vpn by PHP
Enable write access to /var/www by the FTPusers group. It's only one user currently (Myself), with no plans for additional.

Currently /var/www is owned by root, belongs to group root.
Running Apache on Gutsy Gibbon.

I'm rather new to Linux... Can someone please help? Thanks!

With Apache2 on Ubuntu the owner and group for /var/www or the sub-directories should be www-data not root. You need to change this so Apache has write acess. If you want the same access to /var/www as Apache just add the group www-data to your user groups. So issue the following:
```
sudo chown -R www-data:www-data /var/www
```
or to the sub-directories you want Apache to have write access, then:
```
sudo usermod -a -G www-data <name_of_user>
```
read more information in the HTML manual at '/usr/share/doc/apache2-doc/manual'.

---

### Post by warp99 on 2008-05-02
> **rojmab said:**
> Hi, I have tried this:

```
ryan@ryan-desktop:/var/www$ cd ..
ryan@ryan-desktop:/var$ sudo chown ryan www
[sudo] password for ryan:

```

ls -al reveals:
```
drwxr-xr-x  4 ryan root  4096 2008-05-02 08:47 www
```


However, when I ftp to the box, and try to put a file into the www directory, I get permission denied...

```
C:\LocalData\Configs>ftp 10.4.18.100
Connected to 10.4.18.100.
220 Welcome to Ryan's FTP
User (10.4.18.100:(none)): ryan
331 Please specify the password.
Password:
230 Login successful.
ftp> cd /var/www
250 Directory successfully changed.
ftp> put testFile.txt
200 PORT command successful. Consider using PASV.
550 Permission denied.
ftp>

```

Any thoughts? Thanks.

That's a setup issue with your ftp server software, not a permissions issue with your ownership. I would read the documentation on your ftp server. 

Personally I don't use ftp to transfer files back and forth from my machines since the passwords sent are in clear text, instead I use secure shell (SSH) and secure copy protocol (scp) to transfers files.

---

