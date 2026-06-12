---
title: "Mounting remote FTP folder locally"
date: 2016-11-11
forum: General Help
---

### Post by mark120 on 2016-11-11
[COLOR=#333333][FONT=Verdana][FONT=&amp]Hi, I am trying to mount a remote folder on a server I own on my local Ubuntu server

After some research I decided to use the curlftps Debian addon, to try and achieve this.
I was able to manually mount my remote ftp folder to omv by using the command line: {this command line assumes FTP files over TLS }
```

curlftpfs -o ssl -o ssl_control -o no_verify_hostname -o no_verify_peer -d username:password@serverdomain.com:port /mnt/ftpshare

```


I added the username and password to /root/.netrc

```
machine my-ftp-location.local
login myusername
password mypassword

```
And I added the following line to fstab so that the mounting can occur automatically:

```
curlftpfs#user:pwd@myhost:port/folder/ /mnt/ftpshare fuse noauto,user,uid=1000,gid=1000,umask=0022 0 0

```

But I cannot get it to work, can somebody please help me finish the puzzle, I have got this far but I just cant get the final and most important part to work.

Cheers[/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2016-11-11
Purge plain FTP.

Install openssh-server on the remote machine.
Setup ssh client access from your local machine.
Install sshfs on the client, mount using sshfs where you'd like.

If you setup ssh-keys (and you should), it is both highly secure AND more convenient.

OpenSSH is considered secure and doesn't leave any remnants of a protocol that should have died in 1994. All traffic happens over the ssh port, which can easily be changed on the server-side.  Update the ~/.ssh/config file on the clients if you want to automatically fill in a different userid, port, other options, whatever.  Every tool that uses ssh underneath, honors this personal config file - that includes rsync, rdiff-backup and others besides sshfs, sftp, scp, and plain ssh.

---

### Post by ian-weisser on 2016-11-11
TheFu is right. sshfs is secure and easy.

---

