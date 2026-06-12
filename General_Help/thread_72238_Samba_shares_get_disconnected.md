---
title: "Samba shares get disconnected"
date: 2005-10-05
forum: General Help
---

### Post by dang on 2005-10-05
I've been setting up Ubuntu on a box to use as a file server/ftp server etc.
Being a total newbie on linux I've had lots of help reading these forums (thanks for that :)  ).
 
The installation/configuration of Samba worked like a charm, or so I thought...
Usually I can connect to my Samba shares from both my xp box and the ubuntu box itself, but after a while the shares that I've mounted on my xp box are disconnected.
 
Sometimes I can just remount them after a while.
Sometimes I can't connect from my xp box but I can connect from the ubuntu box.
Sometimes i can't reach my shares from either box.
 
Other network apps work just fine.
 
The computers are connected through a switch.
 
I'm puzzled. Does anyone have any idea what might be the problem.
Is it possible that the switch is messing things up?
 
the shares are set up like this:
 
[hdb1]
comment = hdb1
path = /mnt/hdb1
public = yes
writable = yes
valid users = dang
create mask = 0775
directory mask = 0775
force user = nobody
force group = nogroup
available = yes
browsable = yes
 
I'd appreciate any help or input.
thanks
/dang

---

