---
title: "A whole mess of things..."
date: 2006-08-23
forum: General Help
---

### Post by era86 on 2006-08-23
Now I tried searching this on the web, but I can't seem to find a solution. Everytime I try to run an administrative app, instead of gksu popping up and asking me for my password, it simply doesn't load. I don't know if this means anything, but I also keep getting this message when using sudo xxxxx:

sudo: unable to lookup f*******p via gethostbyname()

Has someone ever had such a problem?

Thanks!

---

### Post by ~LoKe on 2006-08-23
Restore your backup of the HOSTS file.

The first uncommented (#) line in /etc/hosts should look like this:
> 127.0.0.1 localhost.localdomain localhost x04d
Replace x04d with your systems' name.

---

### Post by era86 on 2006-08-23
Where is this located. Sorry I'm not familiar with it.

---

### Post by DCM36 on 2006-08-24
> **era86 said:**
> Where is this located. Sorry I'm not familiar with it.

Type or copy this into the terminal:
```
sudo gedit /etc/hosts
```

Then perform the edit suggested by Loke and save.

then you should be ready to go.

---

### Post by era86 on 2006-08-24
Thanks guys that really helped me out alot! Now I backed up my system for nothing.

-era

---

