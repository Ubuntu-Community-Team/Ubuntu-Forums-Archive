---
title: "new mac OS X dmg file??"
date: 2006-08-31
forum: General Help
---

### Post by wakady on 2006-08-31
i've the mac osX 10.4.7 image file, a DMG file i tried to convert it to iso but no luck
i tried to mount it but no luck too, so i checked it with this command
```
file h-t10478.dmg
```
and it gave me this result
```
h-t10478.dmg: bzip2 compressed data, block size = 100k
```

any clue ??

---

### Post by wakady on 2006-09-01
*bump*

---

### Post by Ramses de Norre on 2006-09-01
I have no idea what dmg is, but it seems it's compressed with bzip2?
To uncompress:```
bunzip -kq h-t10478.dmg
```
That will produce an uncompressed file h-t10478.dmg.out, hopefully you will be able to convert/mount that one then.

---

### Post by Ocxic on 2006-09-01
a .dmg file is a disk image for a mac, as far as i know a comp running OS X would mount the file itself, with a ctrl-click and clicking mount, I'm not sure if it's even possible to mount this image in ubuntu. uncompressing it won't help.

---

### Post by fela on 2008-04-04
> **Ocxic said:**
> a .dmg file is a disk image for a mac, as far as i know a comp running OS X would mount the file itself, with a ctrl-click and clicking mount, I'm not sure if it's even possible to mount this image in ubuntu. uncompressing it won't help.

you can mount HFS(+) images (dmg) in Linux with this command: ```
sudo mount -t hfs(plus) -o loop foobar.dmg /path/to/mount/location/
```

---

