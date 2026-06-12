---
title: "images mount problem"
date: 2007-02-14
forum: General Help
---

### Post by dhaus111 on 2007-02-14
Hey all,

I've been trying to mount a cd (Broodwar, yes I know its 10 years old) so I can have a go at installing it with wine.  The image I've got will not mount with 

```
sudo mount -o loop -t iso9660 BROODWAR.ISO /media/img
```

I've got another old ISO that i tried it with (SQL Server) that also didn't work
However I tried it again with Silent Hill and it did work.

i've tried to open open BROODWAR.ISO with Archive manager:
I get CD-ROM is NOT in ISO 9660 format

which complies with what i get when i run the above mount command:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

anybody got any idea as to why these two images are being stubborn? is it even possible that they are not iso9660? Could it have something to do with cd security/anti copy protection?  I'm 100% sure that these images are not corrupt.

thanks for the help

---

### Post by meng on 2007-02-14
If they're not corrupt, perhaps you can burn them to CD ... worth a try.

---

### Post by dhaus111 on 2007-02-15
ok... heres an update.  I'm starting to think it has something to do with the CD copy protection.  I tried to burn it but the image is too big (718MB) for a normal cd.  I'm not sure but I think this is a characteristic of a certain type of cd protection.  I'm thinking this may be confusing the mount command.  After trying to burn, I switched back over to windows and successfully used daemon tools to mount the image and it works fine.  However I know that daemon tools has some workarounds for cd protection built into it that mount may not, or I may just not be specifying the right options.  I'm going to do some googling again here and see what I come up with.

Anybody got any input? Am I completely on the wrong track here?

---

### Post by ashmew2 on 2007-04-02
Same problem...pls help some1...the image is 100% fine and plus its not getting burnt to a cd says "not a valid disc image"

---

### Post by 3rdalbum on 2007-04-02
Have you tried it without the -t iso9660? Not specifying a type means that the Mount command will attempt to discover what type it is.

If that doesn't work, try specifying -t udf instead.

---

