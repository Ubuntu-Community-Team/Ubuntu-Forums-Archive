---
title: "Problems with Samba share with cifs and smbfs"
date: 2006-07-31
forum: General Help
---

### Post by mwtb on 2006-07-31
I have Ubuntu 6.06 installed on my Acer 1682WLMI laptop. My LAN includes a server machine running FC4, with several shares mounted with Samba. Yesterday, I upgraded the packages on the FC4 machine, and these included Samba, which is now at 3.0.23a. Unfortunately, this seems to have broken my mounted shares, which is annoying as I'd only just got them working a couple of days ago. 

 Here's an example of the problem: 

```
$ sudo mount -t cifs //192.168.123.2/hde1 /mnt/hde1 -o username=[myuser],domain=[mydomain],uid=[myuser],gid=[mygroup]
Password:
$ file /mnt/hde1/test.mp3 /mnt/hde1/test.mp3: ERROR: cannot read `/mnt/hde1/test.mp3' (Permission denied)
```

The permissions are correct and in fact, if I simply change to smbfs,this can be demonstrated:

```
$ sudo mount -t smbfs //192.168.123.2/hde1 /mnt/hde1 -o username=[myuser],domain=[mydomain],uid=[myuser],gid=[mygroup]
Password:
$ file /mnt/hde1/test.mp3 /mnt/hde1/test.mp3: MP3 file with ID3 version 2.4.0 tag

```

 So why not use smbfs? Well, because many of the files I have on the shares have foreign characters in them, and smbfs mounts using the settings for unicode as i understand them don't work:

```
$ sudo mount -t cifs //192.168.123.2/hde1 /mnt/hde1 -o username=[myuser],domain=[mydomain],uid=[myuser],gid=[mygroup],
iocharset=utf8
Password:
$ dir /mnt/hde1/MP3/Bj*/ 
/mnt/hde1/MP3/Björk/:

```

Yay!

```
$ sudo mount -t cifs //192.168.123.2/hde1 /mnt/hde1 -o username=[myuser],domain=[mydomain],uid=[myuser],gid=[mygroup],
iocharset=utf8,codepage=unicode,unicode
Password:
$ dir /mnt/hde1/MP3/Bj*/ 
dir: /mnt/hde1/MP3/Bj*/: No such file or directory
```

Boo!

 So, I currently either have a cifs share that allows me to list my files correctly, but doesn't allow me to do anything with them or a smbfs share that lets me use the files, but turns a percentage of my filenames into garbage.

 Is cifs broken on Ubuntu? Is an update due to bring it into line with the latest Samba? Is the FC4 Samba package broken? Have I got all my settings wrong, if so, why was it working before the update?

 Any help appreciated.

---

