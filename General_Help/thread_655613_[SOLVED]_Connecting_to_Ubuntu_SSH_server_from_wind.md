---
title: "[SOLVED] Connecting to Ubuntu SSH server from windows"
date: 2008-01-01
forum: General Help
---

### Post by teryowen on 2008-01-01
Alright so i have a server set up to which i connect through SSH (its Xubuntu 7.10)

when using an Ubuntu machine to connect to it i have no problem i created one of those connection to server icons and it connects fine.

Now i want to do the same from windows perhaps create an icon or a folder which i click on and it connects to the server through SSH, any ideas how to do this? and i don't want the command prompt, i want a folder manager type thing.

Thanks for any help in advance

---

### Post by peitschie on 2008-01-01
I'd recommend WinSCP: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

Its a freeware scp browser ([Screenshots]("http://winscp.net/eng/docs/screenshots")).  Works quickly and reliably in my experience.  You should be able to create a shortcut that you can click on to connect quite easily.

---

### Post by teryowen on 2008-01-01
thanks exactly what i was looking for, any idea of how i would be able to send a kill signal or shut down from this app?

---

### Post by peitschie on 2008-01-01
For that I would recommend Plink which is a command-line interface for putty.  Grab the Plink exe file from the Putty website: [http://the.earth.li/~sgtatham/putty/latest/x86/plink.exe](http://the.earth.li/~sgtatham/putty/latest/x86/plink.exe)
(see [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) for all the downloads)

Then on the windows box, you can do something like:
```

plink user@host sudo shutdown -h now

```

This can easily be set up to run when a shortcut button is clicked or similar.

For more information about what plink can do, see [http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7](http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7)

---

### Post by SOULRiDER on 2008-01-01
I suggest you check out putty.

---

### Post by teryowen on 2008-01-01
alright guys thanks for all the help.

---

