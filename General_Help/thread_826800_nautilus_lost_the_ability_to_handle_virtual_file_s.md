---
title: "nautilus lost the ability to handle virtual file systems"
date: 2008-06-12
forum: General Help
---

### Post by dev.urandom on 2008-06-12
Hello,

After one of the hardy updates, nautilus suddenly lost the ability to handle all virtual file systems and URIs, except for file:///.

ssh:/// or [ftp:///](ftp:///) are treated as syntax errors, and clicking on the trash hangs nautilus.

The "Connect to server" options only shows "Custom location" as the server type.

Does anyone know what might've caused this, and how it can be fixed?

---

### Post by ibuclaw on 2008-06-12
I think ssh and ftp only have two forward slashes infront of them.
ie: **ssh://**  and **ftp://**

And I'm not too sure why clicking on trash hangs Nautilus, its not happening at my end.
How full is the folder?

Also, does pasting this link below into the Nautilus location bar give you any results...?
```
davs://storage-file-eu.gmx.com/
```

Regards
Iain

---

### Post by dev.urandom on 2008-06-12
> **tinivole said:**
> I think ssh and ftp only have two forward slashes infront of them.
ie: **ssh://**  and **ftp://**


Not really a problem. nautilus will remove the extra slashes. 

The problem is that nautilus doesn't recognise them anymore. With gnome-vfs, that would mean that gnome-vfs was not installed. Now with gvfs, I made sure that it was installed, and I even reinstalled it, with no success.

> 
And I'm not too sure why clicking on trash hangs Nautilus, its not happening at my end.
How full is the folder?


Trash is empty. The problem with it and the URIs is related

> 
Also, does pasting this link below into the Nautilus location bar give you any results...?
```
davs://storage-file-eu.gmx.com/
```

Regards
Iain

No, same problem. It's not related to any particular remote fs, but to every fs outside of file:///.

---

### Post by itpaul on 2008-09-12
I'll chime in on this thread as well.

I've already had a rant at [http://ubuntuforums.org/showthread.php?t=894377&highlight=ssh+gvfs+handle](http://ubuntuforums.org/showthread.php?t=894377&highlight=ssh+gvfs+handle)


Should I file a bug? Is already being worked on? This really sucks!

---

### Post by Zalbor on 2008-09-12
I read a list of things they hope to have fixed by the next release of Gnome, and that was in it. So yeah, they know about it. :)

---

### Post by itpaul on 2008-09-12
ok

I know I've already said elsewhere that I'm not interested in alternatives. Well, before I continue, I'd like to change that to

"I'm not interested in SSHFS or anything else that runs as slow."

Now that I've hopefully pre-empted the petty morons that invariably hang around on internet forums, I will continue...

If, like me, you want to edit remote text files, check out Bluefish. Its text editor that can open remote locations. At first it seems pretty unwieldy as you have to enter the url of your file in full. However, when you load up your first file, the rest of the directory pops up in the left panel. You can also traverse the directory tree.

Its not instant, but it seems faster that SSHFS.

Testing in progress...

---

