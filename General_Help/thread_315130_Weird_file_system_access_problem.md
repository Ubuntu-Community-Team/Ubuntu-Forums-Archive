---
title: "Weird file system access problem"
date: 2006-12-08
forum: General Help
---

### Post by JulesBl on 2006-12-08
Hi

Just upgraded to 6.10 from 6.06

I now cant edit the configuration files in the file system doing things like "sudo gedit" etc, the file system does not seem to exist if I use the sudo command, its there if I dont, but then I cant save the file since it read only.

Heeeeeelp!!!

Jules

---

### Post by taurus on 2006-12-08
Try to use gksudo instead of sudo when you use the gedit editor!!!

```
gksudo gedit **filename**
```

---

### Post by JulesBl on 2006-12-09
Tried that

Getting these errors

(gedit:5840): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gedit:5840): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

Anybody?

---

### Post by wgscott on 2006-12-09
What happens if you navegate to that directory and isssue

```
sudo touch junk
```?

Does it prompt you for the password?  Does it accept it?  Does it make the file?

---

### Post by JulesBl on 2006-12-09
Askes for the password and creates the file in etc, its like it has something to do with gnome

---

### Post by taurus on 2006-12-09
Applications -> Accessories -> Terminal
```
sudo nano -w **filename**
```

---

### Post by JulesBl on 2006-12-09
Edits the file and save the new contents, no problem

Appears to be a problem with things like gedit.

Jules

---

