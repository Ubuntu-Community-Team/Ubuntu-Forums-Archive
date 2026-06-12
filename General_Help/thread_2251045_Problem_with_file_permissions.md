---
title: "Problem with file permissions"
date: 2014-11-01
forum: General Help
---

### Post by valdo on 2014-11-01
Hi there this is my first post than sorry in advance if my English and my Knowledgement are no good.
Recently i broke my second hardisk on my ubuntu server that i'm using as multimedia server, below my preview working configuration that is made by a friend that is a linux genius, now he's not able to help me so i try to ask u.
Second Hardisk sdb1 mounted as "multimedia" in /home/user/multimedia
On multimedia i have smb share for read and write files from my imac and nfs server cuz my old tv have an usb-emulation that bring nfs-share as usb source
Actually i'm using deluge server to download my torrent directly on multimedia.
So when the hardisk died i put a comment "#" for the sdb1 mount in fstab and i make rwxrwxwrx (maybe i need less permission) on the /home/user/multimedia
All seems to work fine, i can read and write from mi imac (same user credentials), deluge can put files in the directory and my tv can see the share, but...   every file that deluge download have rwxrwx--- permission and my tv is not able to play them, if i put read permission for others users via chmod (rwxrwxr--) my tv play correctly all files.
So i don't know what was changed from "multimedia" as mounting directory to real directory but i want to avoid to apply permissions with chmod to all file downloaded by deluge.
I'm so sorry if my message is a mess and for my bad english but i should be glad if someone can help me.
Thx in advance Valdo

---

