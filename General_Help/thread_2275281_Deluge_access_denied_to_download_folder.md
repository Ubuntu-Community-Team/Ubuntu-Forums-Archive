---
title: "Deluge: access denied to download folder?"
date: 2015-04-25
forum: General Help
---

### Post by Euphoria on 2015-04-25
Hi all!

I have a personal ubuntu 14.04.2 server with deluge daemon/web for remote access download. I use the startup script from deluge wiki ([http://dev.deluge-torrent.org/wiki/UserGuide/Service/Upstart](http://dev.deluge-torrent.org/wiki/UserGuide/Service/Upstart)) and all working fine. I choose diferent hdd and create a folder for download but when im add a .torrent got permision denied and cannot download. The folder structure are:

/storage/personal/torrents/temp.

/storage: is where the other hdd are mounted, i do it from setup with ext4.
/personal: my personal folder with all my stuff shared with samba. user/group are euphoria (my user) and permision are 750 i can access from my windows.
/torrents and recursive: torrent folder with deluge user/group and 770 permision (i try with 777 but also not work)

i also add my euphoria user to deluge group so im can delete or move downloaded files.

Any idea why deluge cannot write to torrents folder?

Thx. in advance

---

### Post by Euphoria on 2015-04-26
After made some test, i add euphoria group to deluge user and now i can download. -but are this bad security? now the deluge user can access to all my euphoria files.

Is this recomended?

---

### Post by sandyd on 2015-04-26
If the download folder is owned by deluge:deluge, you should be able to download to the folder. euphoria should be able to access the folder if it is chmoded 770 and deluge is one of the groups in euphoria. 

Try
```

sudo gpasswd -d deluge euphoria
su - deluge -s/bin/bash
```

Now, cd to /storage, and then /storage/personal, and so on.

If that works, then we can do a few more tests.

---

### Post by Euphoria on 2015-04-26
Thx. for help, this is my actual setting:
```
$ id euphoria
uid=1001(euphoria) gid=1001(euphoria) groups=1001(euphoria),112(plex),113(deluge)
```
```
$ id deluge
uid=106(deluge) gid=113(deluge) groups=113(deluge)
```
```
$ ls -l
drwxr-x---  4 deluge   deluge   4096 Apr 26 12:41 torrents
```
with your 1º command im remove deluge user to euphoria group. Now deluge user can only acces to torrents folders and sub-folders. euphoria can read it. Thx. for the command

2º i dont understand for whats it is, when i create deluge user im use :
```
sudo adduser --system --group --home /var/lib/deluge deluge
```
with this im create a user without shell access, i thing this is ok for the security.

Any other step?

---

### Post by sandyd on 2015-04-26
Nope, should be fine now.

Side note: Creating a system user (i.e. --system) causes there to be no shell.

The -s flag, when used with su can be used to specify a shell when you actually do need it.

---

