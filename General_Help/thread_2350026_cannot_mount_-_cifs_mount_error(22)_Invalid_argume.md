---
title: "cannot mount - cifs: mount error(22): Invalid argument..."
date: 2017-01-20
forum: General Help
---

### Post by flex567 on 2017-01-20
I am trying to mount a location but it doesn't work?

```

seba@seba-H81-D3:/$ sudo mount.cifs //10.100.31.28 /data -o user=s3809 
Password for s3809@//10.100.31.28:  *********************
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by aromo2 on 2017-01-20
you have to provide the name of the share on the CIFS server that you want to mount.  Example
```
[COLOR=#000000][FONT=&quot]sudo mount.cifs //10.100.31.28/my_share /data -o user=s3809[/FONT][/COLOR]
```

---

### Post by flex567 on 2017-01-20
thanx now it works

---

