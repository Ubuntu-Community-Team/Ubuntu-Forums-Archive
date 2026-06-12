---
title: "Mounting CD burned in windows messes filenames"
date: 2007-06-29
forum: General Help
---

### Post by kung fu buntu on 2007-06-29
I've tried a lot of things, but none seem to work.
Initially I did not even get proper casing of filenames, but I've been able to solve that one. The problem now seems to be with the charset.

I don't know if that is a mount issue or a local issue. My keyboard works ok in X and console (I'm using a portuguese keyboard), although the locale is set to en_US.ISO-8859-15 (I like my software in "internet language" :-)
But unfortunately I still don't have access to the euro char... It gets me the 1/2 char :-(

These commands get me the same result.
[B]sudo mount -t iso9660 -o ro,map=o  /dev/cdrom /media/cdrom0/
sudo mount -t iso9660 -o ro,map=o,iocharset=iso8859-15 /dev/cdrom /media/cdrom0/[/B]

ls /media/cdrom0/ gets me:
**ch¢.txt**
instead of
**chá.txt**

Thanks.

---

