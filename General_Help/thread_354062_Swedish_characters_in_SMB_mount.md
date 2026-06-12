---
title: "Swedish characters in SMB mount"
date: 2007-02-05
forum: General Help
---

### Post by refactored on 2007-02-05
Hi, I've read some threads about mounting SMB shares but I can't get this to work properly. I have a DLink DNS 323 NAS which uses SMB shares. I've come to the point where the following lines have been added to the smb.conf:

```

[global]
unix charset = utf8
display charset = utf8

```

This gives me the correct characters when using smbclient or smbtree but when mounting using one of the following commands (and a bunch more) it just won't work:

```

mount -t smbfs //{IP}/Music ~/SMB/Music
smbmount //{IP}/Music ~/SMB/Music
smbmount //{IP}/Music ~/SMB/Music -o iocharset=utf8 

```

Konqueror shows the correct characters as well.

/refactored

---

### Post by keithweddell on 2007-02-05
Have you tried mounting with cifs?  [This thread]("http://www.ubuntuforums.org/showthread.php?t=288534&highlight=cifs") has a good howto.

Keith

---

### Post by refactored on 2007-02-05
Yes I did try that one out. Got:

```

$ sudo mount -t cifs //D1/Music ~/SMB/Music -o guest,iocharset=utf8,file_mode=0777,dir_mode=0777
retrying with upper case share name
mount error 6 = No such device or address

```

So are you saying that there is no suport for this using mount, smbmount or smbmnt? Would be nice to know if so.

/refactored

---

### Post by keithweddell on 2007-02-06
From the error message, it looks like your {IP} or more likely share name is wrong.  That's why you get the errors "retrying with uppercase share name" and "No such device or address".  Try using the numerical IP address (e.g. 123.123.123.123) and check what the share is called in smb.conf.

Keith

---

### Post by refactored on 2007-02-06
It does not matter what I use, keep getting the same error. And as I can access it using smbclient with either ip or name I belive the problem lies elsewhere.

What differs between smbclient and smbmount? They clearly behave differently.

/refactored

---

### Post by refactored on 2007-02-07
Tried two fuse file systems, smbnetfs and fusesmb. Both handles the encoding correctly but for some reason I can't use them for streaming (and I have to be root).

/refactored

---

