---
title: "Ssh client  (graphic)"
date: 2005-08-29
forum: General Help
---

### Post by skatedawe on 2005-08-29
Hi, i need a program for ssh. I don't want a deamon thing with terminal and shit  :grin: I would like a clean program with menus and options.

 I had this program (WinSCP) for windows, i need a similar program for linux. 
I need it to connect to a hosted webserver. 

 In KDE you could type like fish://user@host.com ... Something like that. Is there any webbrowser adress to work with Gnome like in KDE?

---

### Post by izmaelis on 2005-08-29
Try
```

# ssh remote.host.on.the.net

```
or I don't get your point. If you need a client for Windows use PuTTy.

---

### Post by skatedawe on 2005-08-29
[QUOTE=izmaelis]Try
```

# ssh remote.host.on.the.net

```
or I don't get your point. If you need a client for Windows use PuTTy.[/QUOTE]

 hm, okey. It was meant for linux. Or I need it for linux.

 I'm getting in with term with that command, but i would like like a nautilus pop up or a program where i can drag n drop files, more like a ftp client.

---

### Post by arnieboy on 2005-08-29
[QUOTE=skatedawe]hm, okey. It was meant for linux. Or I need it for linux.

 I'm getting in with term with that command, but i would like like a nautilus pop up or a program where i can drag n drop files, more like a ftp client.[/QUOTE]
use gftp. that will be handy enough.
u can also type in nautilus:
sftp://site_name.abc
and a popup will come asking for user name and password. save ur password and u can use this as a networked folder in nautilus.

---

### Post by skatedawe on 2005-08-29
[QUOTE=arnieboy]use gftp. that will be handy enough.
u can also type in nautilus:
sftp://site_name.abc
and a popup will come asking for user name and password. save ur password and u can use this as a networked folder in nautilus.[/QUOTE]

 You can't ssh with sftp, that an other protcol ?

---

### Post by arnieboy on 2005-08-29
[QUOTE=skatedawe]You can't ssh with sftp, that an other protcol ?[/QUOTE]
u wanted a ftp clone didnt u? thats why I proposed this. but sftp and ssh work hand in hand. sftp is the ftp protocol for ssh servers.

---

### Post by GTvulse on 2005-08-29
[QUOTE=skatedawe]
 In KDE you could type like fish://user@host.com ... Something like that. Is there any webbrowser adress to work with Gnome like in KDE?[/QUOTE]

With Gnome? Transfering files? Is the menu option **Places->Connect to server...** graphical enough fer ya? Now, if you want a **terminal emulator**, opening a terminal emulator and typing *ssh blah* or *sftp blah* is the proper *Unix Zen(tm)*. If you expect something like putty, you can compile it yourself (it builds OOTB under Linux), but you won't get nothing more than a glorified terminal emulator with integrated ssh. Gnome's Terminal is nicer, IMO.

Now, fish is an anomaly of nature, a major hack to simulate FTP with scp, as SSH protocol 1 servers do not have ftp services. As most people use OpenSSH these days, and OpenSSH is a full implementation of both SSH v1 and SSH v2, why would you want to use SSH v1 when you can use SSH v2? If you need to sacrifice security for speed, then I'd say, use Blowfish as the encryption algorithm with SSH v2 before even considering using SSH v1.

---

### Post by skatedawe on 2005-08-29
Thanks I got it now.

---

### Post by techflat on 2006-12-03
Hi there. I wanted to share my experience, but I don't want to duplicate entries. Here's my experience:

[http://ubuntuforums.org/showpost.php?p=1839830&postcount=10]("http://ubuntuforums.org/showpost.php?p=1839830&postcount=10")

---

