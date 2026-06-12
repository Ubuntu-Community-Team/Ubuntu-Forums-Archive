---
title: "How to copy files between ubuntu machines to a share"
date: 2018-09-14
forum: General Help
---

### Post by josephmmorgan on 2018-09-14
All my machines are Ubuntu 18.04.  Typically I employ sneaker net with a USB drive to copy files, but that is tedious at times.  I thought it easy to just setup a share and copy files to those places on other machines where I frequently exchange info. 

So I created a share to a directory on one of my machines.  I can see the share from other machines, but when I try to copy files to that directory, I get an error:

[INDENT]Error while copying to "DirectoryName"
The destination is not a folder.
[/INDENT]

The share is most definitely a folder.  What am I missing here?

---

### Post by HermanAB on 2018-09-14
You want to know the easy way?
Start the SSH daemon and copy the files around with scp.  The scp or sftp protocol is supported natively by the Linux file browsers, so you can even use click drag drop.

---

### Post by SeijiSensei on 2018-09-14
I recommend NFS rather than Samba or any Windows protocol if all your machines run Linux.

For one-off transfers, I suggest using [rsync]("https://linux.die.net/man/1/rsync").

---

### Post by josephmmorgan on 2018-09-15
This sounds like the way I want to go, but I tried the following:

     sudo systemctl start ssh  <= Failed to start ssh.service:  Unit ssh.service not found
     sudo service ssh start     <= Failed to start ssh.service:  Unit ssh.service not found
     sudo /etc/init.d/ssh start <= Command not found.

Is the SSH start something new in 18.04?

---

### Post by josephmmorgan on 2018-12-18
Sorry it has been so long since this reply, as nothing seemed to work... until I finally looked at the bottom of the file manager screen and saw the little (almost completely unnoticeable) "Connect To Server" at the bottom.  One quick "sftp://serverip" and I was set.   Thanks for the reply.    

I suspect, then, I can uninstall samba if all my machines are Linux, right?

---

