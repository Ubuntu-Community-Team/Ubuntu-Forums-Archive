---
title: "path of network folders"
date: 2008-02-07
forum: General Help
---

### Post by lsutiger on 2008-02-07
I connected to a network folder on a server via places-->Network-->Windows Network--><Name Of Network>--><server name>-->Right clicked on share-->Connect to this server-->Enter Name
Now I have this folder on my desktop.

I have tried to access it via CLI doing an ls in the Desktop directory....nothing is there.
How would I access this folder via CLI?

---

### Post by chrisccoulson on 2008-02-07
Good question. I'm not sure you can, as I think this is a limitation of gnome-vfs. If you want to access it via the command line, you will probably have to mount the Samba share (assuming it is Samba, of course) or use some of the command line Samba tools.

It would be worth searching on the forums for mounting Samba shares.

Sorry, I can't help you further.

---

### Post by bwtranch on 2008-02-07
I guess it's just a "virtual folder" and isn't recognized by the directory. Maybe you could try and save it to somewhere and then look.

---

### Post by lsutiger on 2008-02-07
Ah yes, Samba!

I will try tomorrow. The last time I tried that though, the domain wouldn't let me log back in when in Windows - said I had a security breach going on...that was some time a[URL="http://ubuntuforums.org/showthread.php?t=526319"]go.
Follow this link[/URL] to find out what I am talking about.

I will try tomorrow.
Thanx for the input!

---

