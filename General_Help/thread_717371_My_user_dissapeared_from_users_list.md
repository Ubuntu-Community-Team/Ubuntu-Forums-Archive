---
title: "My user dissapeared from users list"
date: 2008-03-06
forum: General Help
---

### Post by jpangamarca on 2008-03-06
Hi, I have this problem: I was trying remastersys and seemingly I didn't have enough disk space to do so. When I ran "sudo remastersys dist", the computer hanged, and I had to change to other terminal (Ctrl+Alt+F2) and reboot, When I got back to Ubuntu, I got a message that I had ran out of space in /home, so I ran "sudo remastersys clean". I had free space again, but now my user disspeared from the face browser in the login screen and the Users and Groups dialog   (In that dialog only root user is listed, but not mine.) This is the screen capture, my user (juanpablo) should be listed here but it's not: [http://jpangamarca.wordpress.com/files/2008/03/pantallazo-opciones-de-los-usuarios.png](http://jpangamarca.wordpress.com/files/2008/03/pantallazo-opciones-de-los-usuarios.png)

When I run "cat /etc/passwd" I get this:

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
messagebus:x:103:109::/var/run/dbus:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
gdm:x:108:118:Gnome Display Manager:/var/lib/gdm:/bin/false
**juanpablo:x:500:1000:Juan Pablo Angamarca,,,:/home/juanpablo:/bin/bash**
oracle:x:501:1001::/usr/lib/oracle/xe:/bin/bash
```

I remember that when the computed hanged running remastersys I got a message that said "uid 500 is not unique" or something like that, I don't remember exactly.

I still can login though, using the default login screen or pressing Ctrl+Alt+Fn, but I want my user listed again, so I can use the face browser and the Users and Groups dialog. Any help will be greatly appreciated.:)

---

