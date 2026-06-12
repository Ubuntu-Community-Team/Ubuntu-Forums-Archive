---
title: "configuring terminals"
date: 2007-06-12
forum: General Help
---

### Post by dominator22 on 2007-06-12
My current set-up is like this; 

getty on 1-6
vt on 7
messages on 8
vt on 9-11
mgetty on 12

This is how I want to change it: 

getty on 1-3
vt on 4-9
mgetty on 10 
messages on 11
kernel logs on 12

How do I do it?  Thanks.

---

### Post by tagra123 on 2007-06-14
> **dominator22 said:**
> My current set-up is like this; 

getty on 1-6
vt on 7
messages on 8
vt on 9-11
mgetty on 12

This is how I want to change it: 

getty on 1-3
vt on 4-9
mgetty on 10 
messages on 11
kernel logs on 12

How do I do it?  Thanks.

for the getty on 1-3
open /etc/inittab

comment out these lines

#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

---

### Post by dominator22 on 2007-06-14
> **tagra123 said:**
> /etc/inittab

Ubuntu doesn't use it.

---

### Post by tagra123 on 2007-06-14
LTS uses it -- depends on your version.
Ubuntu Dapper Does -Feisty doesnt.

Try this

cd /etc/events.d

sudo mv tty4 ~/tty4
sudo mv tty5 ~/tty5
sudo mv tty6 ~/tty6

if it doesnt work you can move them back.

---

### Post by dominator22 on 2007-06-14
> **tagra123 said:**
> LTS uses it -- depends on your version.
Ubuntu Dapper Does -Feisty doesnt.

Try this

cd /etc/events.d

sudo mv tty4 ~/tty4
sudo mv tty5 ~/tty5
sudo mv tty6 ~/tty6

if it doesnt work you can move them back.

This'll just stop the gettys from running.  I want to automatically load multiple X sessions.  
Do I run ```
exec /usr/bin/startx -depth 24 -dpi 96
```?
Or should I run gdm?  ```
exec /etc/init.d/gdm start
```, 
from within /etc/event.d/tty4-9?  Thanks.

EDIT: In a related matter: How do I tell Ubuntu to allow me to run an x session from a console, regardless of how many x sessions are running?

---

### Post by dominator22 on 2007-06-14
> **tagra123 said:**
> 
Ubuntu Dapper Does -Feisty doesnt.

That's why I specified what I'm using in my profile.  It's displayed in every post.

---

### Post by tagra123 on 2007-06-14
Done helping.  Better attitude = more help.

---

### Post by x1a4 on 2007-06-23
> **dominator22 said:**
> My current set-up is like this; 

getty on 1-6
vt on 7
messages on 8
vt on 9-11
mgetty on 12

This is how I want to change it: 

getty on 1-3
vt on 4-9
mgetty on 10 
messages on 11
kernel logs on 12

How do I do it?  Thanks.

```
[tcsh]~/%ls /etc/event.d/
```
control-alt-delete  rc0  rc2  rc4  rc6         rcS          sulogin  tty2  tty4  tty6
logd                rc1  rc3  rc5  rc-default  rcS-sulogin  tty1     tty3  tty5  tty6.dpkg-dist
```
[tcsh]~/%su - root
```
Password: 
```
[tcsh]/root/# cp /etc/event.d/tty[456] /bkp/.dotfiles/titties
```
```
[tcsh]/root/#vim /etc/event.d/tty4
```

#start on runlevel 2
#start on runlevel 3
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 2
stop on runlevel 3
stop on runlevel 4
# stop on runlevel 5
stop on runlevel 6

#respawn
#exec /sbin/getty 38400 tty4

(Copy to tty5, tty6,...)

```
[tcsh]/root/#vim /etc/gdm/gdm.conf-custom
```
[servers]
0=Standard
1=Standard
2=Xgl
#=Standard || Xgl

[server-Xgl]
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true


(Respawn mgetty on tty10)

etc...

---

