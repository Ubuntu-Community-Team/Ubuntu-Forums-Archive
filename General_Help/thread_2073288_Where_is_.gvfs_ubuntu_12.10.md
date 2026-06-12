---
title: "Where is .gvfs ubuntu 12.10?"
date: 2012-10-19
forum: General Help
---

### Post by CrusaderAD on 2012-10-19
Does anyone know where this directory has gone to? It used to be ~/.gvfs

---

### Post by raja.genupula on 2012-10-19
as i have seen in launchpad , there are lot of bugs about this . may be you should have to wait some more time .

---

### Post by CrusaderAD on 2012-10-19
Bummer. There's got to be a way to navigate the smb shares from filezilla. Do you know another way?

---

### Post by Frogs Hair on 2012-10-19
The directory appears in home hidden folders on my 12.10 installation but is empty in may case.

---

### Post by CrusaderAD on 2012-10-19
> **Frogs Hair said:**
> The directory appears in home hidden folders on my 12.10 installation but is empty in may case.

Did you encrypt your home directory during installation? I did, maybe that has something to do with it?

---

### Post by mc4man on 2012-10-19
> **Frogs Hair said:**
> The directory appears in home hidden folders on my 12.10 installation but is empty in may case.

Is that a new install using the release image?
I see .gvfs in a 2 week old install however on a new install yesterday from the 12.10 release it no longer is created

---

### Post by CrusaderAD on 2012-10-19
> **mc4man said:**
> on a new install yesterday from the 12.10 release it no longer is created

Confirmed, this is what I'm running into.

---

### Post by Frogs Hair on 2012-10-19
I let Beta 2 upgrade to final which is probably why the directory is there.

There is a gvfs folder in file system usr/share/gvfs which includes sub folders.

---

### Post by Frogs Hair on 2012-10-19
[https://launchpad.net/ubuntu/quantal/+source/gvfs](https://launchpad.net/ubuntu/quantal/+source/gvfs)

---

### Post by LewisTM on 2012-10-19
The gvfs folder is now in /run/user/<you>/gvfs
Just look at the output of
```
mount | grep gvfs
```
And FYI removable media are now in /media/<you>
Just so you don't spend too much time looking :)

Cheers!

---

### Post by CrusaderAD on 2012-10-19
Excellent, Thanks LewisTM!

---

### Post by james_mcl on 2012-10-20
Is ~/.local/share/gvfs-metadata/ also missing in action as of 12.10?

---

### Post by wheadom on 2012-10-24
Thanks for the information. My share is to an IBM AS/400 (iSeries, IBMi) and (for some reason) I can't set the permissions of files there to executable. I need to execute a shell script, so resort to a desktop shortcut and the sh command.

Moving the mount points isn't too bad (though why they couldn't go somewhere simpler such as /home/<user>/mnt perplexes me), but I notice that the directory name for the mount is some thing like:

smb-share:domain=wwwwww,server=xxxxxx,share=yyyyyy,user=zzzzzzz

not exactly a handy path name. When it was 'share on server' it required quoting because of the spaces (for which I can't think of a useful purpose). I'm equally perplexed why it can't be the simple:

/home/<user>/mnt/server/share

---

### Post by dino99 on 2012-10-24
* debian/gvfs-backends
    - added usr/lib/gvfs/gvfsd-recent
    - added usr/share/gvfs/mounts/recent.mount

 -- Brian Curtis <bcurtiswx@ubuntu.com>  Fri, 20 Jul 2012 12:29:15 -0400

now ~/.gvfs is no more used and can be deleted

---

### Post by LewisTM on 2012-10-24
According to me, the reason they moved the gvfs-fuse mounts outside of home is twofold:

1) Being full of foreign file systems with weird permissions, it would make most backup programs puke when they were asked to backup the home folder by the user.

2) NFS mounted homes could not support gvfs. Most NFS shares don't allow root access and gvfs requires it for mounting.

Why they named it with such complicated syntax, I don't know. You can make a symlink to it and put it in your home folder. You will need to use the terminal
```
ln -s "/run/user/<you>/gvfs/<complicated name>" ~/<insert-simple-name-here>
```

---

### Post by linuxgeoff on 2013-06-16
You guys have to be kidding me?  so, anything that relied on the last version of gvfs (e.g. a bansheee database playing from a NAS) now has to be recreated because you decided to move it?  Wonder why Linux distos haven't taken off for home users? Ask me in a few hours when I've rebuilt all my databases.  grrrrrrrrrrrrrrrrr :-(

---

