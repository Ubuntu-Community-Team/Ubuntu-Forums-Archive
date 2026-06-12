---
title: "How do I do mount a remote FTP drive manually?"
date: 2019-03-11
forum: General Help
---

### Post by texpat on 2019-03-11
I'm on Xubuntu 18.04.2 LTS. In Thunar I can put a remote FTP drive into the location selector like so:

```
ftp://12.34.56.789
```

I'm prompted for my credentials and then I'm ready to go. 
I found I can right click for a context menu that gives me the "open terminal here" option. 
When I do that I have all my terminal commands which I can unleash on the remote files which is awesome, since FTP alone is limited.
My prompt looks like so:

```
user@machine:/run/user/1000/gvfs/ftp:host=12.34.56.789$
```

which tells me the drive is somehow mounted on my file system. I would like to be able to do that manually, from a terminal, without havinng to go through Thunar.
I researched a little and found references to curlftpfs and sshfs, but since they're not installed on my machine, I'd rather use native commands.

---

### Post by yapidumoac on 2019-03-11
```
$apt-get install curlftpfs
$mkdir /mnt/ftp.local
$curlftpfs user:pass@ftp.remote.site /mnt/ftp.local
```

---

### Post by DuckHook on 2019-03-11
@ yapidumoac

Without code tags, your output gets garbled by the forum parsing routines, so please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by texpat on 2019-03-12
Hi @yapidumoac and thanks for your input. I'm aware of that possibility. Wanted to go with something existing rather than installing new software. I'll give it a try if I don't find any other alternative.

---

### Post by Holger_Gehrke on 2019-03-12
If you look at the prompt you get in a terminal, you can tell that 'gvfs' (GIO virtual file system) is involved. So you can either use the (old and deprecated, but still available) 'gvfs-mount' or the new 'gio' command. Both should be installed by default on XUbuntu (they are installed on my system and I don't recall installing them or anything that would have pulled them in). Be aware though that gvfs has a well-deserved reputation for being slow and somewhat buggy for big transfers.

Holger

---

### Post by texpat on 2019-03-12
Thanks @Holger_Gehrke, that's what I was looking for!

---

### Post by texpat on 2019-03-12
> **texpat said:**
> , that's what I was looking for!

Having said that, I found [FONT=Courier New]gio[/FONT] to be quite daunting and the help/man pages beyond my level of expertise. So I tried [FONT=Courier New]curlftpfs[/FONT] and found it quite easy, so for now, I'll be going with that.

---

### Post by Morbius1 on 2019-03-12
Something like this doesn't work?

```
gio mount ftp://username@ipaddress
```

---

### Post by texpat on 2019-03-13
> **Morbius1 said:**
> Something like this doesn't work?

```
gio mount ftp://username@ipaddress
```

Actually, it does. I somehow got tangled up trying to do [FONT=Courier New]**gio -mount**[/FONT] ... 
Something I notice, however, is it wants to mount at the fixed location [FONT=Courier New]**/run/user/1000/gvfs/ftp:host=...**[/FONT] which is not a problem, just another thing that caught me off guard and had me scratching my head for a while ;-)

So now I have **two** ways of mounting remote ftp directories! Thanks to all!

---

