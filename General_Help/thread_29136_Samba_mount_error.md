---
title: "Samba mount error"
date: 2005-04-23
forum: General Help
---

### Post by chryz on 2005-04-23
Attempted to mount  a shared samba folder permanently with rw using the commands described in the starter guide (have both client and server packages installed), but it doesn't seem to work. I get referenced to dmesg which contains the following error message:
        smbfs: mount_data version 1684370019 is not supported

Browsing via Gnome seems to work fine, but since it refuses to give me write access to the files I'm out of luck.

Google says the error message means that the needed commands are missing, and indeed most of them are. Anyone else seen this one - seem kind of odd that I would need to compile my own Samba just to get it to work?

---

### Post by orion_114 on 2005-04-24
I mounted files using this command:

```
smbmount [COLOR=Blue]//computername/sharename /mount/to/location/[/COLOR] -o username=guest%,fmask=644,dmask=755,uid=1000,gid=1 00, debug=0,workgroup=[COLOR=Blue]mshome[/COLOR]

```
Let me know if it works or not ?
(Change the sections in blue for your network)

---

### Post by ifrflyer on 2005-04-24
Might be something really simple: have you got smbfs installed on your machine? It's the utility that lets mount and samba discuss things. Do 

```
cat /proc/filesystems | grep smbfs
``` 

If this doesn't result in 

nodev   smbfs

then do 

```
sudo apt-get install smbfs
```

Hope that helps. If not come back!

---

### Post by crazybill on 2005-04-24
Sounds like you need to modify your samba config files. 
Goto [http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by chryz on 2005-04-26
[QUOTE=ifrflyer]Might be something really simple: have you got smbfs installed on your machine? It's the utility that lets mount and samba discuss things. Do 

```
cat /proc/filesystems | grep smbfs
``` 

If this doesn't result in 

nodev   smbfs

then do 

```
sudo apt-get install smbfs
```

Hope that helps. If not come back![/QUOTE]

Great, and it was embarrasingly simple - smbfs was missing. I saw it working via Gnome and assumed it was allready there.  ](*,)

---

