---
title: "Graphical SSH client?"
date: 2005-05-25
forum: General Help
---

### Post by zcox on 2005-05-25
I'm starting work on a contract in which I need to ssh into a remote server.  I know I can use ssh/scp/etc. via command-line, but are there any ssh clients for Linux with a GUI?  Anything like [WinSCP](http://winscp.net/eng/index.php)?

---

### Post by shakin on 2005-05-25
Well, WinSCP only does file transfers, right? No problem. In the Gnome Places menu you can connect to server and select SSH (or SFTP?) as a server type, then you'll get a shortcut on your desktop to it. IMO, it's even better than WinSCP because it's easier to use, though I suppose it doesn't work as well if you have lots of servers you need to connect to because it will fill up your desktop with shortcuts.

For KDE you can use the K menu -> Network Folders -> Add Network Folder. It will add an entry in the Network Folders submenu and you can drag that onto your desktop or anywhere else to make a shortcut. IMO, this is slightly better than Gnome's implementation since you're not forced to have a desktop shortcut to it.

If you're looking for something similar to Putty to manage console SSH connections, try SecPanel SSH frontend. It's in the repositories as 'secpanel'.

---

### Post by ounn on 2005-05-28
Hi.
Is there a way to make my network servers avaiable from the computer icon on my desktop instead of putting all that drives in my desktop?
I know i can remove them, but i like to access them from the computer icon like i do for my local drives.

Thanks

ounn

---

### Post by kingzasz on 2005-05-28
[QUOTE=zcox]I'm starting work on a contract in which I need to ssh into a remote server.  I know I can use ssh/scp/etc. via command-line, but are there any ssh clients for Linux with a GUI?  Anything like [WinSCP](http://winscp.net/eng/index.php)?[/QUOTE]
 Try putty:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

It runs fine through wine.  So make sure you have wine isntalled, and go to the download location and type "wine putty.exe".  you might have to "chmod a+x putty.exe" first.

---

### Post by daedalus_nl on 2005-05-28
[QUOTE=zcox]I'm starting work on a contract in which I need to ssh into a remote server. I know I can use ssh/scp/etc. via command-line, but are there any ssh clients for Linux with a GUI? Anything like [WinSCP]("http://winscp.net/eng/index.php")?[/QUOTE]

Hi,

You can use [GFTP]("http://www.ubuntuguide.org/#gftp")  This also works with secure file transfer.
or... you can try [SecPanel]("http://www.pingx.net/secpanel/")

---

### Post by arnieboy on 2005-05-29
u can actually use nautilus itself for sftp.. and if u save ur password u are always connected like a normal network folder which can be bookmarked.
then u dont have to use a separate ssh client like gftp.

---

### Post by Moobert on 2005-05-29
in konquerer you can type fish://<ip>:<port> for ssh and sftp...

---

### Post by Tomppa on 2005-06-19
But is there one with resume? Nautilus is works fine, except you cant't interrupt transfer without having to download whole file again. It's really painfull with large files and slow connection.

---

### Post by GilGalad on 2005-06-19
[QUOTE=kingzasz]Try putty:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

It runs fine through wine.  So make sure you have wine isntalled, and go to the download location and type "wine putty.exe".  you might have to "chmod a+x putty.exe" first.[/QUOTE]

You can run the putty linux version (it is in universe repo).

---

### Post by techflat on 2006-12-03
Hello. Here's what I've experienced with ssh.

**Nautilus:**[INDENT]Works fine on Ubuntu Edgy Eft (6.10), not so fine on Ubuntu Breezy Badger (5.10) from what I've experienced. You can access via ssh to your server in two ways.
[LIST=1]
[*]From Nautilus, select File/Connect to Server, the easy way
[*]From Nautilus, typing ssh://user@server
[/LIST]
If your not able to write the address, type CTRL+L and the address bar will appear.
[/INDENT]
**gfpt:**[INDENT]Works fine, but isn't the most stable app... I don't like it that much.
[/INDENT]
**putty:**[INDENT]I've just installed it (apt-get install putty) and it seems to work fine, although I don't see the point, like some of you have said. 
[/INDENT]
**winscp:**[INDENT]I've just installed it, downloaded it from the official site (standalone app), to run it I'm using wine and Crossover. It works fine on both. It's a very cool app, but for practical reasons, I don't know if using it on Ubuntu is worth it, Nautilus works very good.
[/INDENT]

Cheers.

---

