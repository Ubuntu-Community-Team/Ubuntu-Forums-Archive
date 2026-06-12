---
title: "Setting permissions for NTFS subdirectory at boot?"
date: 2008-05-05
forum: General Help
---

### Post by Philosophicles on 2008-05-05
This question relates, thematically, to [this archived thread]("http://ubuntuforums.org/showthread.php?p=4889805").  (The same question is viewable there, but I hadn't realised it was archived, and figured it's unlikely to get a response there.  Apologies if this is a wrong assumption!

I'm assuming that it's still not possible to actually mount subdirectories of a partition at specific places.

In that case, does anybody know if it's possible, having mounted an NTFS partition at, e.g., /windows, to set the *ownership* differently for a subdirectory (my windows 'home' directory) from the partition as a whole (I have a 'windows' user and group that own everything currently)?

With NTFS-3g (stable write-support to ntfs) this would allow me to actually set /windows/[stuff]/[username]/documents to be my home directory, ~, and bypass the need for symlinks from /home/[username] (which has been my solution for a while now).

My aim, of course, is to unify personal files across both my OS environments, as cleanly as possible. A fool's search? Maybe...

---

### Post by maniacmusician on 2008-05-05
I doubt it...it doesn't seem logical to be able to cross-mount a partition in two different places, even if it's just part of a partition.

Why don't you create two NTFS partitions, one for your OS installation, and the other for /home/username? Or better yet, install the ext3 plugin for windows so that you can boot Ubuntu off of an ext3 partition as is recommended. If all you care about is being able to access personal files across both environments, either of these two solutions should work.

---

### Post by bodhi.zazen on 2008-05-05
Not sure what you are wanting exactly ...

> **Philosophicles said:**
> This question relates, thematically, to [this archived thread]("http://ubuntuforums.org/showthread.php?p=4889805").  (The same question is viewable there, but I hadn't realised it was archived, and figured it's unlikely to get a response there.  Apologies if this is a wrong assumption!

I'm assuming that it's still not possible to actually mount subdirectories of a partition at specific places.

You can mount subdirectories of a partition alternate locations.

Example , say your have a partition , call it sda2, mounted at /media/sda2.
Now say there are subdirectories dir1 and dir2 on sda2 and you want to mount dir1 in your home directory ...

```
mkdir ~/dir1

sudo mount --bind /media/sda2/dir1 ~/dir1
```Now contents and Permissions /media/dsa2/dir1 == ~/dir1

> In that case, does anybody know if it's possible, having mounted an NTFS partition at, e.g., /windows, to set the *ownership* differently for a subdirectory (my windows 'home' directory) from the partition as a whole (I have a 'windows' user and group that own everything currently)?

With NTFS-3g (stable write-support to ntfs) this would allow me to actually set /windows/[stuff]/[username]/documents to be my home directory, ~, and bypass the need for symlinks from /home/[username] (which has been my solution for a while now).

My aim, of course, is to unify personal files across both my OS environments, as cleanly as possible. A fool's search? Maybe...Well you have a big problem there. Neither FAT or NTFS support permissions. When these file systems are mounted they are prepared and permissions are set for the entire file system. The only options you have would be dmask and fmask, but you then set permissions for every directory and every file on the NTFS file system.

IMO, the best solution is a /data partition shared between windows and linux with symlinks. Why do symlinks bother you so ? Once they are set they are minimal maintance and invisible. You can link /windows/[stuff]/[username]/documents to ~/documents and it will seem seamless.

---

### Post by maniacmusician on 2008-05-05
> **bodhi.zazen said:**
> Not sure what you are wanting exactly ...



You can mount subdirectories of a partition alternate locations.

Example , say your have a partition , call it sda2, mounted at /media/sda2.
Now say there are subdirectories dir1 and dir2 on sda2 and you want to mount dir1 in your home directory ...

```
mkdir ~/dir1

sudo mount --bind /media/sda2/dir1 ~/home/dir1
```

Now contents and Permissions /media/dsa2/dir1 == ~/dir1



Well you have a big problem there. Neither FAT or NTFS support permissions. When these file systems are mounted they are prepared and permissions are set for the entire file system. The only options you have would be dmask and fmask, but you then set permissions for every directory and every file on the NTFS file system.

IMO, the best solution is a /data partition shared between windows and linux with symlinks. Why do symlinks bother you so ? Once they are set they are minimal maintance and invisible. You can link /windows/[stuff]/[username]/documents to ~/documents and it will seem seamless.

I didn't know about the mount --bind option...is it possible to translate that to /etc/fstab?

---

### Post by bodhi.zazen on 2008-05-05
Absolutely ...

```
/old_location  /new_location  none  bind
```Or in the example I gave :

> /media/sda2/dir1  /home/user_name/dir1  none  bind

:twisted:

---

### Post by Philosophicles on 2008-05-08
@maniacmusician: I will probably give the ext3 plugin for windows a go.  I'm going to be doing all this when I buy a laptop in the near future - right now, I'm just sounding out all the options.  Sorting out a separate partition for 'home' (across both OSes) seems to be the safest option.

@bodhi.zazen: the --bind option was pretty much what I was looking for - totally missed it in the man pages!  Thanks for that, it totally avoids the permissions faff.

[QUOTE=bodhi.zazen]Why do symlinks bother you so ? Once they are set they are minimal maintance and invisible. You can link /windows/[stuff]/[username]/documents to ~/documents and it will seem seamless.[/QUOTE]

I'm not really opposed to them.  It does work seamlessly; I was just wondering if it was possible to *actually* share the 'home' partition/directory directly.

---

