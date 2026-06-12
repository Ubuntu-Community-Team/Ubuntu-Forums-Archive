---
title: "Connecting to Windows Server shares"
date: 2006-11-29
forum: General Help
---

### Post by brottman on 2006-11-29
I am running Ubuntu 6.10 at work where all of our servers are running Windows Server 2003. I am able to connect to the server shares by typing this into Nautilus:

smb://servername/sharename

But when I do, it always asks me to put in my Active Directory user and password. After I type it in, it works for about 10 minutes, then "forgets" my login information and makes me type it in again. How can I get Ubuntu to store my login information or somehow not ask for it and just connect? I've tried checking the box for the keyring but it doesn't seem to actually work.

---

### Post by brottman on 2006-11-29
Would really love to figure this out. What the rest of you who have to connect to Windows shares do?

---

### Post by lordchaos on 2006-11-29
This is how I do it.

Manually:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

On boot:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

Works fine.

---

### Post by brottman on 2006-11-29
I just tried that but all I get is this:

> mount: wrong fs type, bad option, bad superblock on //172.26.1.9/apps,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by brottman on 2006-11-29
Nevermind, this fixed it for me. Thank you very much.

```
sudo apt-get install samba smbfs
```

---

