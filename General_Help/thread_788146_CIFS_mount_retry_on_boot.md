---
title: "CIFS mount retry on boot"
date: 2008-05-09
forum: General Help
---

### Post by tomcheng76 on 2008-05-09
I get this message: 
```

CIFS VFS: Error connecting to IPv4 socket. Aborting operation
CIFS VFS: cifs_mount failed w/return code = -113

```
then it just wait..
As my network share on another pc is not always on, Ubuntu's boot just stop here...
If i press ctrl-alt-del,then i get message like this:
```

CIFS VFS: cifs_mount failed w/return code = -512
rcS (abort/terminated something like that)
rc6 (abort/terminated something like that)

```
then Ubuntu is able to continue the boot process...

What i want is, if my network share is on, auto mount it, if its not, dont mount during boot (no retry or halt...)

Here is my fstab
```

//192.168.0.2/Music                       /media/music   cifs    credentials=/root/.creds,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

Of coz, if i use noauto option, it can boot without problem, but i want auto mount, thanks a lot :)

---

### Post by tomcheng76 on 2008-05-11
Waited one day no reply?
bump.

---

### Post by Zorael on 2008-05-11
As a dirty workaround until someone with actual knowledge of mounting passes by, I guess you could write a script and make it loop itself (or have cron run it occasionally) that checks to see if it's mounted, else mount it. If it's put into [FONT="Courier New"]/etc/rc.local[/FONT], it'll be run with root permissions, so no interaction should be needed.

Hmm.
```
#!/bin/bash

while true;
do
	if [ ! "$(grep //192.168.0.2/Music /etc/mtab)" ];
	then
		mount -t cifs -o credentials=/root/.creds,iocharset=utf8,file_mode=0777,dir_mode=0777 //192.168.0.2/Music /media/music
		break
	else
		sleep 600
	fi
done &
```
I think that might work. I'd save it as [FONT="Courier New"]/usr/local/bin/mountloop[/FONT], make it executable and put a reference to it in [FONT="Courier New"]/etc/rc.local[/FONT].

If you don't want it to break (as in, if you every now and then disconnect 192.168.0.2 and you want the script to remount upon reconnecting it), remove/comment the [FONT="Courier New"]break[/FONT] line and drop the [FONT="Courier New"]sleep 600[/FONT] line outside of the if statement.
```
...

	if [ ! "$(grep //192.168.0.2/Music /etc/mtab)" ];
	then
		mount -t cifs -o credentials=/root/.creds,iocharset=utf8,file_mode=0777,dir_mode=0777 //192.168.0.2/Music /media/music
[B]	fi
	sleep 600[/B]
done &
```


Naturally, modify the sleep duration (in seconds) as you see fit. The script memory overhead would be minute, so you could have it check once every ten seconds, if you so wish.

---

### Post by tomcheng76 on 2008-05-11
I would like to try solution instead of workaround
however, i appreciate your effort, thanks for the script!
i will use it for the temporary solution, thanks again!

---

### Post by Zorael on 2008-05-14
Chancing upon the man page of mount, I see this option:
```
**_netdev**
    The filesystem resides on a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system).
```
That may be what you're looking for. So just place it as an option in its fstab entry.

---

### Post by tomcheng76 on 2008-05-22
Thanks Zorael
i will try that when i arrive home and let you know the result.

---

### Post by tomcheng76 on 2008-05-22
worked as expected. Thank again!

---

### Post by anurag.awasthi on 2012-01-09
Hi Dear,
 
Could you please update me from where I can get the list of CIFS error code with their description. Please help on this query.
 
Thanks in advance.
 
cheers,

---

