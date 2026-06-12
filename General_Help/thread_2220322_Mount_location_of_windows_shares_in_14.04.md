---
title: "Mount location of windows shares in 14.04"
date: 2014-04-27
forum: General Help
---

### Post by lskearney on 2014-04-27
I'm able to open a windows share and view the files contained within from the file manager but I am unable to find the mount point path so that I can cd to in in a terminal window. Normally, i would have expected to find it in /mnt but there is nothing there. Where is it?

Also, what is the appropriate syntax to mount a windows share from the terminal window command line? I tried

sudo mount -t cifs //192.168.1.5/SharedDocs /mnt/share -o o=larry,passwd=xxxxx,rw

but its being rejected.

---

### Post by Morbius1 on 2014-04-27
>                           I'm able to open a windows share and view the files contained within  from the file manager but I am unable to find the mount point path so  that I can cd to in in a terminal window. Normally, i would have  expected to find it in /mnt but there is nothing there. Where is it?
Are you ready ;) It's mounted here:
> /run/user/your-uid/gvfs/smb-share:server=server-name,share=share-name
This whole thing was rewritten while all the adults were on vacation. The old mount point was in a hidden directory within one's home directory but at least it didn't have ":" and "=" signs in it.
> sudo mount -t cifs //192.168.1.5/SharedDocs /mnt/share -o o=larry,passwd=xxxxx,rw
I assume you meant this:
> sudo mount -t cifs //192.168.1.5/SharedDocs /mnt/share -o **[COLOR=#0000cd]username[/COLOR]**=larry,**[COLOR=#0000cd]password[/COLOR]**=xxxxx,rw
That will work ( as long as /mnt/share actaully exists first ) but you won't be able to wite to it unless you are root. So you will have to take posession of the mounted share:
> sudo mount -t cifs //192.168.1.5/SharedDocs /mnt/share -o **[COLOR=#0000cd]username[/COLOR]**=larry,[COLOR=#0000cd]**password**[/COLOR]=xxxxx,rw,[COLOR=#0000cd]**uid=1000**[/COLOR]
Assuming you are uid=1000.

---

### Post by TheFu on 2014-04-27
So ... where things get mounted depends on the program doing the mounting.  gvfs, mount, autofs all have different features.  You **can** control where things go using autofs and mount, but not-so-much for gvfs.

When using gvfs, things mount in a new place like Morbius says.  I've created a softlink to that location from the old location to keep my scripts working and sanity. ;)
For the other 2 methods, the 'df' command will show the mount location - so it will never be a mystery again.

---

### Post by lskearney on 2014-04-27
Thanks, Morbius. I've been working with various flavors of Linux, Solaris, and Unix for 20 years and this one is a new one for me. Who decided this was a good idea?

---

