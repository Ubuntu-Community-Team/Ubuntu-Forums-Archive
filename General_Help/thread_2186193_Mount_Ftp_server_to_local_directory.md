---
title: "Mount Ftp server to local directory"
date: 2013-11-06
forum: General Help
---

### Post by forza.stiinta on 2013-11-06
I need to map a FTP folder to a local directory. I have been using 13.4 with curlftpfs, but after upgrading to 13.10 curlftpfs is very slow.  I have enabled debug and i can see that the curlftpfs ia trying to make lota of connections to random ports.  Think thisbisbwhy it is slow.  I have another 13.4 machine and on n that onr i do not get the strange connections and it is very fast. 

I need an alternative to curlftpfs, or a way to optimise it. 
Thanks,

---

### Post by Lars Noodén on 2013-11-06
If you have SFTP running on the other machine you could use SSHFS to mount the other machine's directory as a local directory.

---

### Post by btindie on 2013-11-06
You could probably just use the internal gvfs-mount program to achieve the same. It's what Nautilus uses when you do File -> Connect to Server

To mount it from the terminal you can just use
```
gvfs-mount ftp://anonymous@ftp.uk.debian.org/
```
which makes it accessible under ~/.gvfs/FTP\ on\ ftp.uk.debian.org/

e.g.```
user@localhost:~$ ls -1 .gvfs/FTP\ on\ ftp.uk.debian.org/debian
dists
doc
indices
ls-lR.gz
pool
project
README
README.CD-manufacture
README.html
README.mirrors.html
README.mirrors.txt
tools
```
To unmount it use
```
gvfs-mount -u ftp://anonymous@ftp.uk.debian.org/
```

---

### Post by forza.stiinta on 2013-11-06
> **Lars Noodén said:**
> If you have SFTP running on the other machine you could use SSHFS to mount the other machine's directory as a local directory.

I do have SFTP but it is much slower than FTP.


When mounting with Ubuntu native way, it looks that somehow it knows that i am using a remote location. For example I cannot drag& drop a file into the web brower, while with curlftpfs i could. Or if I set the option not to show thumbnails on remote locations with curlftpfs it would show thumbs, as it does not know it is remove, while with Ubuntu native mount it will not show the thumbs.

Overall I have seen that before 13.10 curlftpfs was better as performance than ubuntu mount.

---

### Post by forza.stiinta on 2014-02-03
Found this post on another forum. Revert to the older version of the package like instructed there and all problems are solved [http://forum.xbmc.org/showthread.php?tid=176334](http://forum.xbmc.org/showthread.php?tid=176334)

---

