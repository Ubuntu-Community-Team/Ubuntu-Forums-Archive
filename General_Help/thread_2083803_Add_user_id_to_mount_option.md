---
title: "Add user id to mount option?"
date: 2012-11-13
forum: General Help
---

### Post by lars.modig on 2012-11-13
Hi,

I just aided a NAS to my LAN at home. I mounted it under /mnt/Network/ with full rights for all users on my desktop. However I cant use freefilesync to backup my files, but I found a thread at [http://sourceforge.net/p/freefilesync/support-requests/61/]("http://sourceforge.net/p/freefilesync/support-requests/61/") related to my problem. There a guy says that he solved that by.
> Therefore I added my user id to the mount options: uid=1000
Now it works.
I tried to reach him without success so now I wonder if someone within Ubuntu forums can tell me how I manage this within Ubuntu 12.04. I guess it's piece of cake for someone more into this than me...So please a step by step guide would be appreciated.

Now I can only use Freefilesync as root and then of course the access level of my backuped data is not accessible if I'm not root.

Thanks for your help,

/Lars

---

### Post by dannyboy79 on 2012-11-13
what type of sharing does your NAS have? NFS or SAMBA? ALso, is there a config file for freefilesync that would allow you to set the umask?

---

### Post by lars.modig on 2012-11-14
> what type of sharing does your NAS have? NFS or SAMBA? ALso, is there a config file for freefilesync that would allow you to set the umask? 

Well now you display my ignorance to everybody...

I guess that is SAMBA, this is what I added in the fstab.

```
//192.168.1.12/backup /mnt/Network smbfs file_mode=0777,dir_mode=0777,username=admin,password=password,iocharset=utf8 0 0
```

Regarding config file for FreeFileSync and umask I have no clue...

Sorry.

I can also tell you (that may help) that in case I browse the network I can access the nas either via AFP or CIFS. What that means I also dont know...

Br,
The ignorance Lars

---

### Post by rubylaser on 2012-11-14
You can determine your user's umask by typing this in the terminal.
```
umask
```

---

### Post by lars.modig on 2012-11-14
```
lars@lars-MS-7678:~$ umask
0002

```

---

### Post by dannyboy79 on 2012-11-14
> **lars.modig said:**
> Well now you display my ignorance to everybody...

I guess that is SAMBA, this is what I added in the fstab.

```
//192.168.1.12/backup /mnt/Network smbfs file_mode=0777,dir_mode=0777,username=admin,password=password,iocharset=utf8 0 0
```

Regarding config file for FreeFileSync and umask I have no clue...

Sorry.

I can also tell you (that may help) that in case I browse the network I can access the nas either via AFP or CIFS. What that means I also dont know...

Br,
The ignorance Lars
i've heard that "cifs" is faster in performace to the deprecated "smbfs" so you may want to change that. THe same mount options still work. So you would just add uid=1000,gid=1000 assuming your users and group is is 1000 which on most ubuntu installations it is. That should do it.

---

