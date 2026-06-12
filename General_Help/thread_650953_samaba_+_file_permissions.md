---
title: "samaba + file permissions"
date: 2007-12-27
forum: General Help
---

### Post by t3hi3x on 2007-12-27
I have a nice little web server thats running on 1u server. i have a limited amount of space in it so i bough a 750 gb hd to put in another server of mine. I am using torrent flux and anyone who knows how it works, the user www-data writes files. Every time I mount the smb folder it only make root the owner and chown and chmod return this:

```
chown: changing ownership of `t3hi3x`: Operation not permitted
```

here is my command I am using to mount the sucker:

```
sudo mount -t smbfs -o username=apbresh,password=$$$$$$ -o owner=www-data //192.168.1.144/disk /var/www/jbuflashradio_com/torrents/downloads/t3hi3x
```

mounts great, but only root can make changes :(

Does anyone know how to make it where www-data can make changes?

---

