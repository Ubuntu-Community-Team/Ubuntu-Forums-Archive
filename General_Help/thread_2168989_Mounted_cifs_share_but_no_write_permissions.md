---
title: "Mounted cifs share but no write permissions"
date: 2013-08-20
forum: General Help
---

### Post by mortuk on 2013-08-20
Have reinstalled Ubuntu on my web dev server. On the old one I had an smbfs share setup to access a share over the local network to other Ubuntu boxes. It was setup using the following and worked fine - [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This time round I am using cifs-utils instead of smbfs, but I presume this is fine?

Upon reinstalling the server I have been having issues making the files writable. Its mounted ok, and when from my local machine I ls -l it shows me write permissions (although from my local user), but when I goto create or save over a file it gives me a no permissions error

Here is the line in my /etc/fstab. I had to make one change to be able to mount, and I added the ,sec=ntlmv2 option, without which I was getting mount error(13)

```
//192.168.0.40/webserver    /media/webserver        cifs    credentials=/root/.smbcredentials,sec=ntlmv2,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0
```

and my credentials file (unchanged from when it was previously working)

```
username=melon
password=xxxxxxxxxxxx
```

How can I fix it so that I have write permissions on my mount?

Also on askubuntu if anyone wants rep :) - [http://askubuntu.com/questions/334422/mounted-cifs-share-but-no-write-permissions](http://askubuntu.com/questions/334422/mounted-cifs-share-but-no-write-permissions)

---

### Post by TheFu on 2013-08-20
If you want complete control over file permissions on multiple Linux systems shared on the same internal network, NFS is 1000x better than Samba/CIFS.  NFS will make native file permissions available on the shared storage. The exact same owners, rwxrwxrwx permissions work on the client machines as on the servers.  For many years, places where I've worked mounted my HOME across many different servers - all UNIX/Linux ... 1 home, regardless of the actual machine ... this was accomplished via NFS.  Plus, it really isn't hard to setup.

I've only used samba to share files with Windows machines.  The /etc/samba/smb.conf file is where all the permissions for each shared area are located. Never used cifs-utils, but I'd expect something similar. 
Is there a conf file that you can post?
Are there log errors that you can post?

---

### Post by Morbius1 on 2013-08-20
Assuming you haven’t done something to the server folder permissions that prohibits a write to user: melon you might want to add yet another option to your growing list: nounix.

```
//192.168.0.40/webserver    /media/webserver        cifs    credentials=/root/.smbcredentials,sec=ntlmv2,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=1000,gid=1000,[COLOR=#0000cd]**nounix**[/COLOR] 0 0
```

---

