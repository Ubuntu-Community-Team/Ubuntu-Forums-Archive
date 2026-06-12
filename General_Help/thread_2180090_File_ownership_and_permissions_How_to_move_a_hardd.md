---
title: "File ownership and permissions: How to move a harddrive to another linux machine?"
date: 2013-10-11
forum: General Help
---

### Post by silentcreek on 2013-10-11
Hi,

I have a rather basic question. I have a linux server and want to move its harddrive into a new ubuntu machine. The old server provides maily samba shares and backups via rsnapshot. Most files on the drive are owned by the samba user.
My question is this: When I move the drive to the new server, how can I make sure, that the files and scripts work the same way as before.
My plan is to create a user for samba on the new machine with the same username. But is that enough to retain the previous permissions or do I have to worry about userids (uid) or something like that? Or, to put the question differently, if I create a user with the same name on the new machine, will the new machine automatically treat the files on the drive as if they were created by the user of the new machine? What about files that belonged to root before?
Btw, I only have three users on the old machine, if that matters at all.

Thanks,

Timo

---

### Post by JKyleOKC on 2013-10-11
> **silentcreek said:**
> 
My question is this: When I move the drive to the new server, how can I make sure, that the files and scripts work the same way as before.
My plan is to create a user for samba on the new machine with the same username. But is that enough to retain the previous permissions or do I have to worry about userids (uid) or something like that? Or, to put the question differently, if I create a user with the same name on the new machine, will the new machine automatically treat the files on the drive as if they were created by the user of the new machine? What about files that belonged to root before?It's almost, but not quite, enough. The system actually works on user **NUMBERS** called UIDs instead of the names themselves, since the number can be stored in two bytes while the name could be of any size and having a fixed size greatly simplifies searching and matching.

UIDs start with 1000 and go up from there as you add users. You can go into a terminal and type "cat /etc/passwd" to get a listing that looks similar to this:```
jk@mehitabel:~$ cat /etc/passwd |grep ":10"
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:107::/var/run/dbus:/bin/false
avahi-autoipd:x:103:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:105:46:usbmux daemon,,,:/home/usbmux:/bin/false
haldaemon:x:106:113:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:107:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:108:114:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:109:116:RealtimeKit,,,:/proc:/bin/false
[COLOR="#FF0000"]jk:x:[COLOR="#00FF00"]1000[/COLOR]:1000:Jim Kyle,,,:/home/jk:/bin/bash
testu:x:[COLOR="#00FF00"]1001[/COLOR]:1001:Test User,,,,:/home/testu:/bin/bash
[/COLOR]jk@mehitabel:~$ 

```Those last two lines (the ones in color) are the two users on this system of mine. The others, with UIDs below 1000, are system users that operate behind the scenes and were automatically generated at install time. For each line, the first number (in green) is the UID and the second the GID or group ID.

To make everything work as before, you have to make sure that the UID on the new system matches that on the old. The actual name can vary so long as the UID matches. The easy way to make certain of a match is to create the users on the new system in the same sequence as those in the old; to verify, repeat the command I used above on the new system.

The UID for "root" is 0, and will be the same on the new system, so those files will remain as before.

Hope this helps!

---

### Post by silentcreek on 2013-11-19
Thanks, it worked as described. I set up the users with the same uids on the new Ubuntu Server and everything is running smoothly.

---

