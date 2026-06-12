---
title: "lost permisions"
date: 2007-09-13
forum: General Help
---

### Post by DANGISE on 2007-09-13
I was unable to load flash player for linux. followed instructions from "kilz" and loaded swiftweasel 32. now flash works but lost some permissions. when i try to move some desktop icons to the trash I get an error: Cannot move "/home/user/..._i386.deb" to the trash because you do not have permissions to change it or its parent folder. I get similar errors for different icons. How can I fix this?

---

### Post by thedarkwinter on 2007-09-13
Hi

I imagine some of the things or part of the process was using sudo permissions which messed things up a bit. Try opening a shell/konsole and type the command

```
sudo chown -r xxxx:xxxx /home/xxxx
```

where xxxx is your username

good luck

---

### Post by DANGISE on 2007-09-13
tried that and got invalid option

---

### Post by vanadium on 2007-09-13
You better post the errors you get here in the forum. That way people might be able to see what is wrong.

---

### Post by DANGISE on 2007-09-13
Cannot move "/home/user/...nux.tar.gz" to the trash because you do not have permissions to change it or its parent folder.

---

### Post by nick_h on 2007-09-13
chown needs -R not -r for the recursive option

---

### Post by DANGISE on 2007-09-14
-R worked. Thanks for your help.

---

### Post by wscheer on 2007-09-15
Just had that same issue suddenly pop up. 

"sudo chown -R xxxx:xxxx /home/xxxx" worked great. Thanks thedarkwinter

---

