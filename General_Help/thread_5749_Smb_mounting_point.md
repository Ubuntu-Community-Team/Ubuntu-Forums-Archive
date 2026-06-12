---
title: "Smb mounting point"
date: 2004-11-22
forum: General Help
---

### Post by Franz on 2004-11-22
Again in trouble, I hope you will excuse my little sxperience with Linux.
I'd like to mount on my Pc some directories shared by Win users in my LAN. I can see and acces their directories using Nautilus, but if I give the command
sudo mount -t smbfs //wincomputer/shared /mnt/mountpoint
I read this error
mount: wrong fs type, bad option, bad superblock on //wincomputer/shared ,
       or too many mounted file systems
I've tried also with the option 
-o username=username
but with no results.
Can anyone help?
Thanks!!
 ](*,)

---

### Post by p!=f on 2004-11-22
Do you have smbfs package installed and/or smbfs module loaded?
Do you specify a hostname or an IP address for the computer you want to connect to?

---

### Post by jiyuu0 on 2004-11-22
Try:
$ sudo apt-get install smbfs

There are some mount network folders How-Tos here:
[http://kitech.com.my/ubuntu/4.10/index.html#networking](http://kitech.com.my/ubuntu/4.10/index.html#networking)

---

### Post by Franz on 2004-11-23
Thank you very much!! It works!!!
Franz

---

### Post by senectus on 2004-11-23
[QUOTE=jiyuu0]Try:
$ sudo apt-get install smbfs

There are some mount network folders How-Tos here:
[http://kitech.com.my/ubuntu/4.10/index.html#networking](http://kitech.com.my/ubuntu/4.10/index.html#networking)[/QUOTE]

I think I've missed something..
I followed those instructions but when I try to connect to the public shar on my ubuntu laptop from a windows PC I get a popup asking for username and password..
Is there any way to share without the requirements of a username and password (read and write)?
Thanks..

---

### Post by jiyuu0 on 2004-11-23
[QUOTE=senectus]I think I've missed something..
I followed those instructions but when I try to connect to the public shar on my ubuntu laptop from a windows PC I get a popup asking for username and password..
Is there any way to share without the requirements of a username and password (read and write)?
Thanks..[/QUOTE]

Sorry... I've made a mistake

in /etc/samba/smb.conf

change 
security = user

to
security = share

---

### Post by senectus on 2004-11-23
wahoo! that works.. thanks..

---

### Post by jiyuu0 on 2004-11-24
Just up...

More how-tos on sharing files:
[http://kitech.com.my/ubuntu/4.10/#fileserversamba](http://kitech.com.my/ubuntu/4.10/#fileserversamba)

---

