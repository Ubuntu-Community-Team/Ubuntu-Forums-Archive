---
title: "Mounted share is read write only to sudo, need my user to be able to make changes"
date: 2018-11-11
forum: General Help
---

### Post by maxburn on 2018-11-11
I have a 16.04 VM running some automation under my user and a large share of files which is now on a FreeNAS box that replaced a Synology. I can not read/write the share now without elevating to sudo and I don't know why. I didn't have to do that with the Synology.

I used to mount the synology with this in fstab and was able to read write to it with my user

```
#//192.168.1.21/ds418 /mnt/ds418 cifs credentials=/home/myname/ds418creds,iocharset=utf8,sec=ntlm 0 0
```

I shifted to this to mount FreeNAS, which required a higher SMB version. freenascreds contains the user and pass of a read write user in FreeNAS.

```
//192.168.1.23/freenas /mnt/freenas cifs credentials=/home/myname/freenascreds,vers=3.0,iocharset=utf8,sec=ntlm 0 0
```

With this share mounted I simply can't go in to /mnt/freenas anywhere and simply make a file or directory WITHOUT elevating to sudo. Which means my automation things are all erroring out.

BUT I can use windows or solid explorer to mount that share with the same credentials ubuntu is using and make/delete files fine. What is this disconnect I have with Ubuntu?

---

### Post by TheFu on 2018-11-11
Unix systems should use NFS for file sharing. Many reasons for this.

---

### Post by Morbius1 on 2018-11-11
> //192.168.1.23/freenas /mnt/freenas cifs credentials=/home/myname/freenascreds,vers=3.0,iocharset=utf8,sec=ntlm 0 0
Take possession of the mounted share:
> //192.168.1.23/freenas /mnt/freenas cifs credentials=/home/myname/freenascreds,vers=3.0,iocharset=utf8,sec=ntlm[COLOR=#0000cd]**,uid=maxburn**[/COLOR] 0 0
Change maxburn to your Ubuntu login user name.

You may need to add [COLOR=#0000cd]**nounix**[/COLOR] to your list of options but try it without it first.

Side note: sec=ntlm seems a little inconsistent with SMBv3  but if it mounts without errors ......

---

### Post by maxburn on 2018-11-11
> **Morbius1 said:**
> Take possession of the mounted share: **uid=maxburn**


I love you, thanks that did it. So obvious once it's pointed out.

---

