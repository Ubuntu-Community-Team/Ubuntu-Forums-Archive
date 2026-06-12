---
title: "sshfs and secured credential to auto mount NAS shared folder"
date: 2016-12-15
forum: General Help
---

### Post by alain.roger on 2016-12-15
Hi,

i have a NAS with some shared folders.
till now i used the /etc/fstab to mount them as following:

```
[FONT=monospace][COLOR=#000000]//mynas/folder1      /mnt/folder1    cifs iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000 0 0[/COLOR][/FONT]
```

however i read that using sshfs would implement an additional layer of security.
i'm able in terminal to mount the same shared folder as following:

sshfs username@mynas:/folder1 /mnt/folder1 -p sshfs_port

however doing such thing request the password for username.
Is there a way to stored it on a simple txt file (as smbcredentials file) with just 600 as permissions to avoid someone to read credentials/password ?

Or is there a better way ?

thx a lot.

---

### Post by SeijiSensei on 2016-12-15
Use shared keys.  See: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

That, of course, assumes the NAS knows how to handle keys.

---

### Post by alain.roger on 2016-12-15
thx for the link.

i have only 1 stupid question.

when we are transfering the public key there is a sentence in the text as "[COLOR=#333333][FONT=Ubuntu]Where [/FONT][/COLOR]<username>[COLOR=#333333][FONT=Ubuntu] and [/FONT][/COLOR]<host>[COLOR=#333333][FONT=Ubuntu] should be replaced by your username and the name of the computer you're transferring your key to."

username should be the ssh username that already existing on Openssh server or the username i want to use... like for me my default username is : alain but on openssh server ssh username is different.

thx[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-12-15
I assume it's the username you want to connect as.

---

