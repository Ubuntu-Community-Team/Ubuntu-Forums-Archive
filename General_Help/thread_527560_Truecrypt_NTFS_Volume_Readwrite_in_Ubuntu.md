---
title: "Truecrypt NTFS Volume Read/write in Ubuntu"
date: 2007-08-16
forum: General Help
---

### Post by kingleer on 2007-08-16
The reason I'm posting this here is because the linux truecrypt forums are geared towards more advanced users (I'm still kinda of a nooby).

Okay, so I installed truecrypt with no problem. I'm able to mount a truecrypt NTFS partition in Ubuntu and read it's contents. I am unable to write to said partition though. 

I get an error which says 

Error while copying to /home/kinglear/mnt

You do not have permissions to write to this folder 

(see attached pic for screenshot) 


I read somewhere that 

"Yes, people are using ntfs-3g with Truecrypt. The Truecrypt volume must be mounted with the flag --filesystem set to ntfs-3g."

Any advice  on how to write to an NTFS truecrypt partition. 
\

---

### Post by merlinus on 2007-08-16
```

sudo apt-get install ntfs-config

```

then

```

sudo ntfs-config

```

Tick appropriate boxes and restart.

-merlin

---

### Post by kingleer on 2007-08-16
Thanks Merlinus. 

I also think I found a site that backsup your solution

see- 

[http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html](http://hype-free.blogspot.com/2007/04/installing-and-using-truecrypt-on.html)

in particular

If you wish to mount an NTFS formatted volume in read/write mode, you need to have the ntfs-3g driver installed, and when mounting specify it by saying --filesystem ntfs-3g because the autodetect mode will result in the usage of the read-only ntfs driver. Also the user mount option doesn't seem to work for me, so instead you can use the --mount-options gid=100,uid=1000,umask=000 parameter to make it accessible to all the user. You can find out the number you need to type for gid (GroupID) and uid (UserID) by doing a cat /etc/group|grep user and cat /etc/passwd|grep [your user name] respectively.

---

