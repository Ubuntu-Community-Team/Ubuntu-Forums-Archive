---
title: "Transmission cannot write to smb mount"
date: 2016-09-10
forum: General Help
---

### Post by marco2g on 2016-09-10
Hello everyone

I have mounted an SMB share to a ubuntu box running transmission. Unfortunately, transmission cannot write to this share. As a user, I can write to /var/nas (the mountpoint for the share) after adding the gid "nas" to the fstab entry.

I have added my user and debian-transmission to group "nas", however I still receive an error that transmission is unable to write to this share.

Does anybody know how I can make this work?

---

### Post by reese1379 on 2016-09-16
[COLOR=#111111][FONT=Consolas]# try ..
sudo usermod -g sambashare debian-transmission[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-09-16
I strongly recommend you don't write torrents directly to a network share.  It creates an enormous amount of network traffic.  Instead, write the file to the machine's local drive, then move it to the SMB share when it's finished.

Some clients have the option to download to one location but move the file automatically to another location when finished.  Sadly Transmission doesn't seem to have that option.  I think Deluge might though.

---

