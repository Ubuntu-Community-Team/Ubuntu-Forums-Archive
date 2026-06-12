---
title: "how to disable netbios broadcast?"
date: 2017-07-17
forum: General Help
---

### Post by unityforever on 2017-07-17
*Files* will broadcast Netbios request while initializing.

I guess it has something to do with Network browser, the one next to the Trashcan, shown in sidebar.

may i ask how to turn this thing off, im not at my home and i really don't need this function.

---

### Post by TheFu on 2017-07-17
I'm not positive, but ... remove all samba client files.  Of course, this means you won't be able to connect to any Windows shares.

I don't use a GUI for file management.

---

### Post by HermanAB on 2017-07-17
You only need Samba (smbd and nmbd) for connection to Windows servers.  If you don't need it, uninstall/delete it.

---

### Post by Morbius1 on 2017-07-17
Your title and your description don't match. 

To disable netbios broadcasts it's Samba - and only if you run a samba server - not Files that does that and you just have to disable nmbd from running.

But your description talks about Files seeking out or "browsing" for the netbios broadcasts of others.

How about preventing the "browse" function from executing as a normal user:
```
sudo chmod 744 /usr/lib/gvfs/gvfsd-smb-browse
```

---

### Post by unityforever on 2017-07-18
> **Morbius1 said:**
> Your title and your description don't match. 

To disable netbios broadcasts it's Samba - and only if you run a samba server - not Files that does that and you just have to disable nmbd from running.

But your description talks about Files seeking out or "browsing" for the netbios broadcasts of others.

How about preventing the "browse" function from executing as a normal user:
```
sudo chmod 744 /usr/lib/gvfs/gvfsd-smb-browse
```

may be it is because my bad english...
but i do catch the packages sent by Files
when i open it, Files will boradcast some UDP package, i decoded it and the content is :NETBIOS REQUEST
sometimes those broadcasts will attract some Windows computers
they will try to establish connection to me for sending their information and this is a thing i don't wanna it happened.

and i didn't install samba before. the command your guys provided above are invalid, but still thanks for your help

---

### Post by Morbius1 on 2017-07-18
>  and i didn't install samba before. the command your guys provided above are invalid, but still thanks for your help                 
Does that mean you didn't try it?

** The samba client library has been installed by default on desktop Linux for a generation so there was nothing for you to install.
** I ran Ubuntu in a live session to see if the command I gave you was in fact invalid.

It runs, the file exists, and the permissions are changed.
If I try to initiate a browse of the network for samba servers I will get this error message:
[ATTACH=CONFIG]276033[/ATTACH]

---

