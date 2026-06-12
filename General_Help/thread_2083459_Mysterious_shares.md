---
title: "Mysterious shares"
date: 2012-11-12
forum: General Help
---

### Post by dwlamb on 2012-11-12
Recently, I had to do a full format and install to 12.04.  Trying to do an upgrade from 11.04 through the update manager failed.

With this new install, I have downloaded Samba and installed it, but not performed any customisations to get things working.  Mounted on the fstab is a drive formatted to ntfs and was in use on the previous o/s.  A number of the directories on that Windows drive were and still are shared.  I can not change them.

Under My previous installation, Samba was installed but I did the sharing through the Nautilus gui, not through smb.conf. My smb.conf on this new installation is pristine.  If I go through the Nautilus gui, the Sharing Options shows the directories are not shared, yet from another computer on the network, I can open and manipulate these shares with the same privileges I had before as if Ubuntu 11.04 was the o/s.

I have tried manipulating the share through the gui,  sharing the directory and then unsharing, to see if I can get control of the sharing working properly but to no avail

Can anyone point me in a direction to explain this?

---

### Post by ercherramon on 2012-11-12
try to install ubuntu from zero. download the ISO 12.04.1 LTS which is the most updated. Sometimes the upgrade are not very clean and they bring you some headaches later.

---

### Post by bab1 on 2012-11-13
> **dwlamb said:**
> Recently, I had to do a full format and install to 12.04.  Trying to do an upgrade from 11.04 through the update manager failed.

With this new install, I have downloaded Samba and installed it, but not performed any customisations to get things working.  Mounted on the fstab is a drive formatted to ntfs and was in use on the previous o/s.  A number of the directories on that Windows drive were and still are shared.  I can not change them.

Under My previous installation, Samba was installed but I did the sharing through the Nautilus gui, not through smb.conf. My smb.conf on this new installation is pristine.  If I go through the Nautilus gui, the Sharing Options shows the directories are not shared, yet from another computer on the network, I can open and manipulate these shares with the same privileges I had before as if Ubuntu 11.04 was the o/s.

I have tried manipulating the share through the gui,  sharing the directory and then unsharing, to see if I can get control of the sharing working properly but to no avail

Can anyone point me in a direction to explain this?

Samba shares that are created using Nautilus (usershares) are stored at /var/lib/samba.  They are not configured with the /etc/samba/smb.conf file.

As to your probem, I would delete the shares and recreate them,

---

