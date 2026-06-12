---
title: "[ASK] Problem with Tar"
date: 2015-08-25
forum: General Help
---

### Post by thekotaksamapah on 2015-08-25
Hallo master,

I'm new in ubuntu. I have some problem when unzip archive.

```

total 28
-rwxr--r-- 1 root root 10240 Aug 26 10:17 Archive.tar
-rw-r--r-- 1 root root 10240 Aug 26 10:24 data.tar
drwxr-xr-x 2 root root  4096 Aug 26 10:18 Exctract



```

When I extract data.tar to Folder called Extract. I do this

```

root@TBX-Server:/home/thekotaksampah/LatihanZip/Latihan_B# tar -xvf data.tar Exctract/
tar: Exctract: Not found in archive
tar: Exiting with failure status due to previous errors
root@TBX-Server:/home/thekotaksampah/LatihanZip/Latihan_B#



```

am I missing something?

---

### Post by nerdtron on 2015-08-26
syntax to extract:
```
tar -xvf data.tar 
```

syntax to extract to a different folder
```
tar -xvf data.tar -C /path/to/destination 
```

But the destination folder should be existing in order to extract on that location.

---

### Post by thekotaksamapah on 2015-08-26
Thanks for help. It works :D

---

