---
title: "VLC + SMB = problem &quot;streaming&quot; mp3's"
date: 2006-12-29
forum: General Help
---

### Post by lagreca on 2006-12-29
I'm giving Ubuntu a try and am having problems playing mp3's via a SMB share.  If I go to places, network servers, and find music on my fileserver, I am unable to play the mp3's with VLC.  

If I double click on the mp3's, they launch in totem, and seem to play fine.  However if I right click on the mp3 and select "open with other application", then select VLC, VLC launches, however the mp3's do not play.  

This seems like a fairly straight forward operation I'm trying to complete, so I'm not sure why i'm encountering such difficulty.  ](*,)

---

### Post by kd7swh on 2006-12-29
As far as I know VLC doesn't support the Samba protocol. In my case I run apache (web server) on a desktop computer that is running dapper (Ubuntu 6.06). The desktop stores my audio and video content and I can stream it to my laptop (running edgy) using VLC.

Songbird is another program that is very neat. It uses VLC but it also has a built-in browser which makes it easy to browse your collection that is stored remotely.

I hope this helps. I will do some searching and see if I can get Samba to stream with VLC.

---

### Post by ebash on 2006-12-29
There's a bug in ubuntu edgy (6.10) and it can't stream data over SMB, no matter the application being used. The others protocols (http, ssh, etc) are working fine only SMB is affected.

---

### Post by QOLIM on 2006-12-29
1. VLC does support samba
2. there is a bug in a codec lib with streaming from samba but this doesn't affect vlc since it has it's own codecs.
3. To give an answer to the original question,
it is true that you can't open a mediafile using samba from the file browser.
But you can still open it in vlc with open file: smb://*servername*/*location on the server*/*filename*
Another problem is that you can't open a folder on smb with this :( 
you can only open a single file at the time

Possible solution is here: _[http://ubuntuforums.org/showthread.php?t=273206](http://ubuntuforums.org/showthread.php?t=273206)_

---

### Post by lagreca on 2006-12-29
When the known bug is fixed, will I be able to fix my version with the built in ubuntu updater?  

I can open a file from the file browser, if I use the default player, Totem.  I just can't seem to do it with VLC.  Is it typical to not be able to open files via the file browser, or is this a limitation of VLC?  

Thank you for the response!

---

### Post by cids.dk on 2008-05-19
if you mount your smb share on your file system then there shod be no ploblem playing them on vlc.

```
mkdir mp3
sudo mount -t cifs -o user=cid //192.168.1.5/mp3 /home/cid/mp3

```

you will have to put in the password needed by sudo, followed by the password needed for your smb share.

---

