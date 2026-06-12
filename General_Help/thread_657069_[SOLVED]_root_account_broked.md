---
title: "[SOLVED] root account broked"
date: 2008-01-03
forum: General Help
---

### Post by blueyez on 2008-01-03
i played with > System / Administration / Users and Groups ( should not :D )

and now i can't run "things" as root 
using sudo / sudo won't work to...
what have i done ? :D

when i use "sudo su" nothing happens.. 

trying to run System / Administration / Users and Groups a warning message appears: you don't have permission to use this bla bla... 

fix ideas ?

---

### Post by meindian523 on 2008-01-03
Add yourself back to the admin group.After booting in,press Ctrl+Alt+F1,username:root and password whatever you set it to during installation or afterwards.

If you didn't set a password,boot into recovery mode start Xserver using ```
startx
```

I forget the file which enabled root GUI login,anyone?

---

### Post by rubicon on 2008-01-03
Um. Try this: ```
groups <your username>
``` to see the groups you are in.

You can run sudo/gksudo and have administrative privileges if you are in 'adm' and 'admin'.

To add yourself in this groups, you can run ```
sudo adduser <your username> adm && sudo adduser <your username> admin
```. I know, you can't do it now :) So, boot in single-user mode (from GRUB menu) and run ```
adduser <your username> adm && adduser <your username> admin
```

And -- don't play with groups! :)

---

### Post by blueyez on 2008-01-03
ok it works now. but:
> 
root@unix:/# groups blueyez
blueyez : chiuc root adm dialout fax cdrom floppy tape audio dip video plugdev scanner fuse lpadmin admin netdev powerdev samba
root@unix:/# groups root
root : root adm dialout fax cdrom floppy tape audio dip plugdev scanner fuse admin samba


i added myself to a few more groups to be shure that would work :D. wich one should i remove from my account ?

---

### Post by rubicon on 2008-01-03
First tell us -- can you do 'sudo something' now?

The only candidate for removal which I see is group 'root'. Normally you shouldn't be a member of this group.

---

### Post by blueyez on 2008-01-03
yes i can do "sudo"

question: to remove account "blueyez" from group "root" the command is:

> userdel blueyez root

 ???

i don't wanna delete my account :D

---

### Post by p_quarles on 2008-01-03
That won't delete the group or the user, it'll just remove the first from the latter.

But, if you're worried, you can simply delete your name from the first line of the group file:
```
gksudo gedit /etc/group
```

---

### Post by blueyez on 2008-01-03
tkz, one more question and i'm done :D


```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:root,blueyez
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:root,blueyez
fax:x:21:root,blueyez
voice:x:22:
cdrom:x:24:haldaemon,root,blueyez
floppy:x:25:haldaemon,root,blueyez
tape:x:26:root,blueyez
sudo:x:27:
audio:x:29:root,blueyez
dip:x:30:root,blueyez
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:blueyez
sasl:x:45:
plugdev:x:46:haldaemon,root,blueyez
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,root,blueyez
nvram:x:105:
fuse:x:106:root,blueyez
ssl-cert:x:107:
lpadmin:x:108:blueyez
messagebus:x:109:
admin:x:110:root,blueyez
crontab:x:111:
ssh:x:112:
avahi-autoipd:x:113:
avahi:x:114:
netdev:x:115:blueyez
haldaemon:x:116:
powerdev:x:117:haldaemon,blueyez
gdm:x:118:
slocate:x:119:
chiuc:x:1000:blueyez
samba:x:1001:blueyez,root
```

this looks a bit to messy... is ok ?! :|

---

### Post by p_quarles on 2008-01-03
I've seen messier. ;) Looks fine to me.

---

