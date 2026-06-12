---
title: "Ubunutu hangs when running a mv or cp command"
date: 2008-06-26
forum: General Help
---

### Post by infocom on 2008-06-26
Hi

Ubuntu 8 is hanging half way through the following commands which is part of a backup script I am running. Maybe its the cp command thats hanging as there are thousands of files and I would have thought the mv command just renames the folder which shouldnt be a problem? Does anyone know what I can do to find out why it hangs? Thanks

mv /home/myuser/files/5 /home/myuser/files/tmp
mv /home/myuser/files/4 /home/myuser/files/5
mv /home/myuser/files/3 /home/myuser/files/4
mv /home/myuser/files/2 /home/myuser/files/3
mv /home/myuser/files/1 /home/myuser/files/2
mv /home/myuser/files/tmp /home/myuser/files/1
cp -al /home/myuser/files/2 /home/myuser/files/1

---

### Post by rubicon on 2008-06-26
Run commands with -v key, so mv and cp would be verbose. There'd be a lot of text on the screen, but at least you'll know on which stage it freezes.

With -v key means:
```

mv -v /home/myuser/files/5 /home/myuser/files/tmp
...
cp -alv /home/myuser/files/2 /home/myuser/files/1

```

---

### Post by infocom on 2008-06-29
thanks rubicon. i have done this but actually I think Ubuntu is hanging on its own without the above commands. I thought it was the above commands because I have been trying to execute them every time I run Ubuntu. But a few times now I start Ubuntu, login and have just left it for a while. Then when I go back to run these commands its just hung. 

So I think its just hanging on its own.

Do you or anyone know if there are any logs or anything I can find that may show what it was doing before it hangs?

---

