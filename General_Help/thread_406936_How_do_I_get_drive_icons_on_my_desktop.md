---
title: "How do I get drive icons on my desktop?"
date: 2007-04-11
forum: General Help
---

### Post by jakev383 on 2007-04-11
I'm sure this has been asked, but I'm not sure how to find it.
I have an icon on my desktop for a share (see attachment). I added another share to my fstab, but how do I get this icon to show? I know I can put a sym link to it and then change the icon to match, but I don't want the shortcut arrow on the icon. What icons get placed on the desktop have to be in a config file or something somewhere! 
Anyone know where?
Thanks!

---

### Post by nike984 on 2007-04-11
Open "/etc/fstab"
and 
change option "default" to "user" 

Just like this example

from:
/dev/sda6 /media/Win-D vfat default,utf8,umask=007,gid=46 0 0
TO
/dev/sda6 /media/Win-D vfat user,utf8,umask=007,gid=46 0 0

---

### Post by jakev383 on 2007-04-11
> **nike984 said:**
> Open "/etc/fstab"
and 
change option "default" to "user" 

Just like this example

from:
/dev/sda6 /media/Win-D vfat default,utf8,umask=007,gid=46 0 0
TO
/dev/sda6 /media/Win-D vfat user,utf8,umask=007,gid=46 0 0

```

# /dev/sda5
UUID=07E9-9197  /extra          vfat    user,utf8,umask=000,uid=1000,gid=1000 0      0 

```
Didn't work for me.... Anywhere else it could be? I don't have a shortcut or anything on my desktop for this share now - I did, but I removed it. Or does the 'user' flag remove the shortcut arrow?
Thanks.

---

### Post by paparucino on 2007-04-11
> **jakev383 said:**
> I'm sure this has been asked, but I'm not sure how to find it.
 
Anyone know where?
Thanks!
Try this 
```

sudo gconf-editor

```
then
```

apps - nautilus - desktops 

```
On the right window check **[COLOR="Red"]volumes-visible[/COLOR]**

It should work.

---

### Post by jakev383 on 2007-04-11
> **paparucino said:**
> Try this 
```

sudo gconf-editor

```
then
```

apps - nautilus - desktops 

```
On the right window check **[COLOR="Red"]volumes-visible[/COLOR]**

It should work.
That was already checked..... Thanks though!

---

### Post by jakev383 on 2007-04-11
I ended up moving the mounts back to the /media folder and they show on my desktop now. I just had to sym-link them back to where I wanted them to fix all the other stuff I had setup to point at those shares.
Thanks for all the suggestions!
If anyone knows of a better way to put drives on the desktop, let me know!

---

