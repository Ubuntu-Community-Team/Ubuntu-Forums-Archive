---
title: "Where is 'remember this password' saved for network shares?"
date: 2007-11-11
forum: General Help
---

### Post by mikey12345 on 2007-11-11
I've been accessing another linux server's shares on my network and i checked the box that said to remember the password forever.

How do i stop this? I don't want it remembered for security reasons but can't find where to stop it?

Thanks.

P.s. What's the best way to mount the remote share for easy desktop click access?

---

### Post by mahousaru on 2007-11-11
System, Administration, Keyring Manager

If you want to automatically mount the share then you can have a line in fstab with something like

//server/share   /mnt/data   smbfs   credentials=/etc/samba/user,rw,uid=bob   0   0

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Happy_Man on 2007-11-11
Press alt-f2 and enter ```
gconf-editor
```. Then browse to apps/nautilus/desktop and check the network_icon_visible box. That should give the network folders a link on your desktop. As for remember passwords, I would guess in /etc/<whatever app you have saved the password with>

---

### Post by bapoumba on 2007-11-11
> **mikey12345 said:**
> I've been accessing another linux server's shares on my network and i checked the box that said to remember the password forever.

How do i stop this? I don't want it remembered for security reasons but can't find where to stop it?
Which browser are you using? Should be somewhere in prefs or privacy or personal data.

---

### Post by mikey12345 on 2007-11-12
Removed from Keyrings and had to reboot for it to take effect.

Thanks.

---

