---
title: "how to unpack and install .run files?"
date: 2008-07-05
forum: General Help
---

### Post by crazyfuturamanoob on 2008-07-05
I just downloaded wolfenstein:enemy territory linux client. Gdebi can't open it, 
and I don't know how to use terminal. How to unpack and install "et-linux-2.6.0.x86.run", 
which is in my desktop folder?

---

### Post by ibutho on 2008-07-05
You need to do Applications -> Accessories -> Terminal
```

cd ~/Desktop
chmod +x et-linux-2.6.0.x86.run
./et-linux-2.6.0.x86.run

```

---

### Post by cariboo on 2008-07-05
You may have to run the command as root. In a Applications-->Accessories-->Terminal type:

```
sudo ./et-linux-2.6.0.x86.run
```

as it will probably want to install some library files.

Jim

---

### Post by baracuda68 on 2009-04-01
When I just installed the most current version of HPLIP from its website,hplip-3.9.2.run was downloaded.
I went to my terminal, navigated to the folder it was DLéd to, (cd /home/bob/downloads) 
typed sh hplip-3.9.2.run
It went through the automated process, answering different questions for install ,etc.
I didn't even have to change permissions, though you might have to for that package.

---

