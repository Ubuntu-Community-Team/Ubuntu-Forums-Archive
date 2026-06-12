---
title: "Accessing file server with backslash in the path"
date: 2013-10-02
forum: General Help
---

### Post by adam17 on 2013-10-02
Hi,

I am attempting to connect to a network at work on our server share and Ubuntu seems to have a problem with it due to it having backslashes in the path.

On my windows laptop I can go to run or the folder and type \\noxxxxx-xx.net\wxxxxx and it will open the path.

However on Ubuntu if u use the commmand: nautilus network:\\noxxxxx-xx.net\wxxxxx it throws an error. Does anyone know how I can access this folder with the backslash in the path?

Thanks Adam

---

### Post by pholden on 2013-10-02
Assuming you are talking about accessing a Windows share (SMB), then you need to browse to *smb://noxxxxx-xx.net/wxxxxx* in nautilus ;)

---

### Post by adam17 on 2013-10-03
Hi Pholden,

Thanks for the suggestion but unfortunatly this doesnt work either. I am not completely sure what server it is that my company run which obviously make things more difficult, and no one here knows the slightest thing about Linux. 

Adam

---

### Post by steeldriver on 2013-10-03
You can also do it by escaping each of the backslashes with another backslash e.g.

```

$ sudo mount -t cifs **\\\\**NAS-01.local**\\**Public /mnt/cifs/public
[sudo] password for steeldriver:
Password: 
$ ls /mnt/cifs/public/
Program Files  setup  Downloads  Software  Thumbs.db

```

FYI you can use the 'smbtree' program to see what shares the system can see

```

sudo apt-get install smbclient
smbtree

```

---

### Post by adam17 on 2013-10-16
Hi,

Still no joy :( 

when using the smbtree command, I dont see the path I am looking for. I know it is there tho as windows can access it.

---

