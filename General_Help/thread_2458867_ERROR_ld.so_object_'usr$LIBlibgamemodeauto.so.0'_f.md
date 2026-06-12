---
title: "ERROR: ld.so: object '/usr/$LIB/libgamemodeauto.so.0' from LD_PRELOAD"
date: 2021-03-05
forum: General Help
---

### Post by dunivixs on 2021-03-05
Hello,

I use Ubuntu 20.04.2 LTS "Focal Fossa" , 64 bits

I have installed Genshin Impact from Lutris, the launcher works good and I have download it but when I want to launch it, it fails without show a error message.
When I saw the logs, I saw only one error :

"ERROR: ld.so: object '/usr/$LIB/libgamemodeauto.so.0' from LD_PRELOAD cannot be preloaded (cannot open shared object file): ignored."

If you want to see the full logs : [https://cdn.discordapp.com/attachments/434408303817261056/817418882666594314/logs_Genshin_Impact.txt](https://cdn.discordapp.com/attachments/434408303817261056/817418882666594314/logs_Genshin_Impact.txt)
If you don't trust on my .txt file just ask and I will take screenshots.

So to fix it, I saw that video : [https://www.youtube.com/watch?v=ZHh4Zpr59aU](https://www.youtube.com/watch?v=ZHh4Zpr59aU)
I did all the commands
But this does not work, and I noted that the env variable LD_PRELOAD did not exist.
I added ```
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libgamemodeauto.so.0
``` 
on the file ~/.bashrc, without resolution.

Thanks for your help

Dunivixs

---

