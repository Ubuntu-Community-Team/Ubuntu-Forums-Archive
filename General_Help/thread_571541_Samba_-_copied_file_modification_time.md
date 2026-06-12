---
title: "Samba - copied file modification time"
date: 2007-10-09
forum: General Help
---

### Post by rickfitz on 2007-10-09
Having problems with timestamps in a mixed Windows/Ubuntu network. 
No problems accessing samba shares (on Feisty server), but...

If a file is **copied** to a share from a WindowsXP box, the file's mtime on the server is the same as the original source file. So ctime is set by the server, and mtime comes from the client.

Do the same thing from a Feisty box, and mtime is set to the fileserver time, not the original file's time (so it's the same as ctime).

This is driving me crazy - spent all afternoon googling for info but can't find anything relevant. It looks like the smb client doesn't send the mtime to the server. I've tried this with Nautilus using both fusesmb and direct (gnome smb?) but the result seems the same. Also tried using 'cp -a' and 'cp -p' over fusesmb, but makes no difference.

Thanks for any suggestions,
Rick.

---

### Post by gcalis on 2008-01-04
Have a look at the samba [manpage]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") on smb.conf, you'll find some interesting options there among which:
> dos filemode (S)

The default behavior in Samba is to provide UNIX-like behavior where only the owner of a file/directory is able to change the permissions on it. However, this behavior is often confusing to DOS/Windows users. Enabling this parameter allows a user who has write access to the file (by whatever means) to modify the permissions (including ACL) on it. Note that a user belonging to the group owning the file will not be allowed to change permissions if the group is only granted read access. Ownership of the file/directory may also be changed.

    Default: dos filemode = no

dos filetimes (S)

    Under DOS and Windows, if a user can write to a file they can change the timestamp on it. Under POSIX semantics, only the owner of the file or root may change the timestamp. By default, Samba runs with POSIX semantics and refuses to change the timestamp on a file if the user smbd is acting on behalf of is not the file owner. Setting this option to yes allows DOS semantics and smbd(8) will change the file timestamp as DOS requires. Due to changes in Microsoft Office 2000 and beyond, the default for this parameter has been changed from "no" to "yes" in Samba 3.0.14 and above. Microsoft Excel will display dialog box warnings about the file being changed by another user if this parameter is not set to "yes" and files are being shared between users.

    Default: dos filetimes = yes 

Just set 'dos filemode = yes' in smb.conf (/etc/samba/smb.conf). 

Have a look [here]("https://help.ubuntu.com/community/SettingUpSamba") (@ help.ubuntu.com) on how to setup Samba on Ubuntu for more info.

---

