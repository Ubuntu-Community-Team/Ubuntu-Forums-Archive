---
title: "Looking for GUI file browser for my server"
date: 2008-07-09
forum: General Help
---

### Post by Jimbo13 on 2008-07-09
I set up a old PC as a Ubuntu Jinzora media server. I access it from my XP PC but I have many other files, programs etc. on the hard drive in my ubuntu server.

I'd like to use it for all purpose storage besides media. 
Is there a program I can get that will give me A browser and allow me to up and download from the Ubuntu PC and look through the files I have stored?

Preferably something with a GUI that a Linux noob like me can handle.

I already have samba, apache, mysql etc as they are required for jinzora.

Thanks.

---

### Post by comandrei on 2008-07-09
Have you tried Midnight Commander? Otherwise you must install at least a Window Manager such as icewm and a file browser (Thunar, Nautilus or Dolphin).

---

### Post by Jimbo13 on 2008-07-09
I'll give that a google thanks.

Hadn't tried anything yet wasn't sure what to look for.

---

### Post by comandrei on 2008-07-09
You could also install WinSCP on your XP box and a SSH server on the ubuntu server.
[http://winscp.net/eng/docs/screenshots](http://winscp.net/eng/docs/screenshots)
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
I think this will suit your needs better.

---

### Post by Jimbo13 on 2008-07-09
Beautiful, Thanks very much WinSCP is exactly what I was looking for.

---

### Post by Jimbo13 on 2008-07-09
Well I'm up and running logged in with WinSCP but I can't find the second drive on my Ubuntu server.

Am I right thinking it should be in /media? All that's there is cdrom0.

---

### Post by comandrei on 2008-07-09
Get [putty]("http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe"), log on to you server and run
```

df -h | grep /dev/

```
that sould list you your partitions and where they are mounted.

---

### Post by Jimbo13 on 2008-07-09
> **comandrei said:**
> Get [putty]("http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe"), log on to you server and run
```

df -h | grep /dev/

```
that sould list you your partitions and where they are mounted.

Thanks again, I think my problem with my other drive lies in the mount options looking that up now.  The second drive doesn't seem to be active until I select  manually in places

If you ever need any help with video/sound editing send me a PM thats my thing.

---

