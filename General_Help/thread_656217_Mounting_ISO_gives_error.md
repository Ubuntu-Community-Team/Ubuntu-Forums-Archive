---
title: "Mounting ISO gives error"
date: 2008-01-02
forum: General Help
---

### Post by Virtus92 on 2008-01-02
I am trying to mount an ISO-image with first:
```
sudo mkdir /home/kubuntu/lol
```
then
```
sudo mount -t iso9660 -o loop /home/kubuntu/nfsu2.iso /home/kubuntu/lol

```

But it gives me this error: ```
kubuntu@localhost:~$ sudo mkdir /home/kubuntu/lol
kubuntu@localhost::~$ sudo mount -t iso9660 -o loop /home/kubuntu/nfsu2.iso /home/kubuntu/lol
mount: Not a directory
kubuntu@localhost:~$

```
What can I do? I've already tried AcetoneISO2, but that gives another error (see attachment)
With AcetoneISO2 I tried both options (convert tab and activating fuse), but none worked.
Plz help me!

---

### Post by cdenley on 2008-01-02
Are you sure /home/kubuntu/lol is empty? Post the output for:
```

ls -a /home/kubuntu/lol
ls -ld /home/kubuntu/lol

```

---

### Post by Virtus92 on 2008-01-02
It's empty:
```
kubuntu@localhost:~$ ls -a /home/kubuntu/lol
.  ..
kubuntu@localhost:~$ ls -ld /home/kubuntu/lol
drwxr-xr-x 2 root root 4096 2008-01-02 16:10 /home/kubuntu/lol
kubuntu@localhost:~$

```

---

### Post by cdenley on 2008-01-02
That command worked fine for me. You must have a bad iso.

---

### Post by bulletxt on 2008-01-03
if you have done step c as acetoneiso2 error says, it is quite sure you have a bad image. anyways allways with acetoneiso2 try to convert it under "convert" tab and see what happens.

---

