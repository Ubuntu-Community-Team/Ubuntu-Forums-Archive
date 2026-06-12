---
title: "Accessing Windows Share for Password Safe Data"
date: 2008-04-08
forum: General Help
---

### Post by Nick w on 2008-04-08
I have Password Safe running on my Ubuntu PC at work. I use password safe as do some of the other IT guy in the office, at the moment the only way to access the Password Safe .psafe3 file is to have it local on my machine as it cant see the windows share its located in

BUT because other staff update the file on the windows share i have to copy it locally. and when i update it i have to copy it back

is there any way of getting password safe working in WINE that can access the windows sharE?

Thanks

---

### Post by cdenley on 2008-04-08
create a mount point and install smbfs
```

sudo mkdir /media/myshare
sudo apt-get install smbfs

```

add this line in /etc/fstab
```

//fileserver/myshare /media/myshare cifs uid=1000,username=myuser,password=mypass 0 0

```

then mount it
```

sudo mount /media/myshare

```

You're system won't know the difference between files on your local system, and files on the mounted share. All files for that share will be in /media/myshare.

---

### Post by Nick w on 2008-04-08
thanks very much for the quick reply
but im getting this error:

unknown filesystem type 'cifs'

any ideas?

thansk
nickhttp://ubuntuforums.org/editpost.php?do=editpost&p=4676890

---

### Post by cdenley on 2008-04-08
Sorry, i forgot you need this package
```

sudo apt-get install smbfs

```
I will edit my previous post.

---

### Post by Nick w on 2008-04-08
getting closer :)

new error:
nick@NWU0450:~$ sudo mount /media/Technology
cli_negprot: SMB signing is mandatory and we have disabled it.
18067: protocol negotiation failed
SMB connection failed

---

### Post by Nick w on 2008-04-08
i ****** up worked great
THANKS SOOOOOOO MUCH

---

### Post by Nick w on 2008-04-08
Thanks soo much again. Well chuffed :)

---

