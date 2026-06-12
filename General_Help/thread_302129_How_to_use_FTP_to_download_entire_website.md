---
title: "How to use FTP to download entire website"
date: 2006-11-18
forum: General Help
---

### Post by Ted_Smith on 2006-11-18
I want to download ALL  files and ALL directories from my website using the FTP command (gFTP keeps crashing). 

After connecting I've tried 'mget *', 'mget *.*', 'mget -r *' and many other combinations, and all I've managed to do is download a handful from the root of the site, and even then I have click 'yes' for each one. 

I've read the Linux in a Nutshell book, and several entries on the Internet, but they all say things like "To download multiple files that all have the extension jpg type 'mget *.jpg'" etc. I cannot find one entry where it says "To download your entire website using FTP type this command...". 

Can anyone help? 

Thanks

Ted

---

### Post by huygens on 2006-11-18
Hi,

If you're not afraid of the command line, I would suggest that you install ncftp. It is not Open Source, but it is free (you don't have to pay), it's available in universe and it is a neat ftp client.
You would not have problem to use it. For installation and usage simply type this (it is assume your ftp server is ftp.ted_smith.org and the user is ted_smith):
```
sudo apt-get  install ncftp
ncftp -u ted_smith ftp.ted_smith.org
**ncftp / > **get -R *
```The text "**ncftp / >**" represents the "prompt" from ncftp, don't type it, just type "get -R *".

Huygens

---

### Post by Ted_Smith on 2006-11-18
That's great huygens - thanks a lot. I have tried that and it has worked. The only problem is that the connection was closed half way though the download. Any ideas how to get round that?

Ted

---

### Post by koenn on 2006-11-18
can't help with the connection going down. 
maybe just try again ?

also :
wget is a very good command line tool to download entire websites. It uses http by default.

---

### Post by huygens on 2006-11-19
> **Ted_Smith said:**
> That's great huygens - thanks a lot. I have tried that and it has worked. The only problem is that the connection was closed half way though the download. Any ideas how to get round that?

So you have the disconnection even with ncftp? I have no idea why the server would close the connection.

What I can imagine is that your client "overload" the server. I mean that there are some configuration possibilities within FTP server that drop a connection if the session time, session CPU consumption, etc. reach a certain limit. So perhaps, the FTP server of your host has such a restriction. The only way to circumvent it would be to download in several steps your web site.
So for example let say you have several directories at the root of your web site. You could launch a "get -R <direction name>" command under ncftp for each of those directories. But remember that between each command you might have to quit and reconnect, so the session resources consumption are reset...

I hope you get the point :-)

Huygens

---

### Post by bliffle on 2007-11-21
"wget" will do all you want and more, and it's in every linux/unix system and has been implemented on most mainframes as well. I've also seen it on Windows and OS2 (Warp). Hunt around for posts on 'wget' or just RTFM! Give yourself a chance and type in a CLI "man wget". Try it, you'l like it.

---

