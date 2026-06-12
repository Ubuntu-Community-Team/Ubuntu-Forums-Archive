---
title: "The right Network procotol: DAV, SSH, SMB"
date: 2007-02-04
forum: General Help
---

### Post by AllBuntu on 2007-02-04
Since I have enough computers to run a small country, I have been wanting to pick a good network protocol for some time. I just did. And my preference will be
1. WebDAV
2. SSH
3. SMB
4. E-Mail...

HARDWARE and SOFTWARE
My operating systems are Linux (Ubuntu), Windows XP, and Mac OS X 10.4.8
Ubuntu and OS X supports all three, while DAV clients for Windows are all buggy and some payware. DAV is one of those things Microsoft has little interest in having functional, because it makes Windows networking instantly obsolete.

[INDENT]a. WebDAV means w3c's protocol with Apache as the server going over https. It is hard to find two WebDAV end-points that play together but Apache2 and davfs2 seems to work. Apache runs everywhere but takes configuration, and again no DAV client for Windows other than the browser.

b. SSH also has support on Ubuntu-OS X while for Windows OpenSSH freeware is server and scp is what you got for a client. 

c. SMB is well supported on Windows and OS X, while on Ubuntu it is challenged in term of file name capabilities and domain authentication. I would say avoid.
[/INDENT]
TESTING
So what I did: I hooked up an Edgy laptop to a Dapper server over 100 Mb/s Ethernet using sshfs, samba, and davfs2. Then I copied an about 725 MB file twice for each protocol and noted elapsed time for the second copy.

SSH - 4.8 MiB/s
```
sshfs daboy@1.0.0.8:/var/dav ssh
time cp ssh/MyDocuments/Outlook/Mail\ 2005\ Official.pst .
```

SMB - 4.6 MiB/s
```
mount: sudo mount -t smbfs -o username=daboy,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000 //xpc21/daboy smb
time cp smb/MyDocuments/Outlook/Mail2005Official.pst .
```

WebDAV - 7.5 MiB/s (maybe not comparable)
```
mount -t davfs https://1.0.0.8/dav/ dav
time cp dav/MyDocuments/Outlook/Mail\ 2005\ Official.pst .
```
This DAV implementation is very different, it caches everything. So the first time you get 2.3 MiB/s, and then you get 7.6 MiB/s with virtually no network activity (and that's for a GiB.) However, since it's WebDAV, I could double-check downloading with Firefox cranking out a healthy 7.5 MiB/s. If you every used the iDisk on the Mac this is it.

AND THEN
I did not do NFS and Appletalk reading a couple of horror stories. However, I always thought SMB would be the fastest for some reason. In this case not so.

---

