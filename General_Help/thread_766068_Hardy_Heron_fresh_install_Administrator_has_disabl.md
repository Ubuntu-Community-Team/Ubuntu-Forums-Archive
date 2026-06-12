---
title: "Hardy Heron fresh install: Administrator has disabled your account"
date: 2008-04-25
forum: General Help
---

### Post by ArtPulse on 2008-04-25
Hey there! I've just put in Ubuntu 8.04 Hardy Heron Desktop Live CD, formatted my old ubuntu 7.10, installed this one instead with the Installer (not through the "live desktop", but the second option at the CD boot)... and...

installation is over, I restart... awesome, it's there, boots... kay, GDM splash, let's log in...
user: pulse
password: my password xP

and a dialog sth about I don't have a home directory and begs me to press Yes :S then another dialog comes out, click on OK, then I get a "The administrator has disabled your account" :S OK, and i go back to GDM splash :S

I try to go to console with Alt + F1, yet I can't log in as i get some error about $HOME= whatever, it seems I dont have a home xP and I can't log in to root either, so I can't log in ANYWHERE to do a sudo or a su or be a root to actually change the users!! >.<

So how do I fix this? It's a fresh install, i couldn't try it yet =( help me!! ;(

---

### Post by xaenyx on 2008-04-25
It sounds like maybe your installation was corrupted..  Faulty CD maybe?

Anyway, if all else fails, try booting from a (new) ubuntu cd, mount the HD, and then make the home directory (and set permissions).

---

### Post by ArtPulse on 2008-04-25
yeah, i have created /home/pulse/ and chmod it to 777 just to be sure xP yet... no response...

these are screens of what i get:

[[IMG]http://img167.imageshack.us/img167/3553/dsc01757az6.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=dsc01757az6.jpg)  [[IMG]http://img91.imageshack.us/img91/3314/dsc01758bw5.th.jpg[/IMG]](http://img91.imageshack.us/my.php?image=dsc01758bw5.jpg)  [[IMG]http://img110.imageshack.us/img110/7003/dsc01759ji7.th.jpg[/IMG]](http://img110.imageshack.us/my.php?image=dsc01759ji7.jpg)

=(!

---

### Post by Distro Jockey on 2008-04-25
I would suggest trying with a different username.
pulse is also the name of a default group in Hardy used by PulseAudio.

---

### Post by FredB on 2008-04-25
Yes, indeed :

```
fred@fred-laptop:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:fred
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:fred
fax:x:21:
voice:x:22:
cdrom:x:24:fred
floppy:x:25:fred
tape:x:26:
sudo:x:27:
audio:x:29:pulse,fred
dip:x:30:fred
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:fred
sasl:x:45:
plugdev:x:46:fred
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:fred
ssl-cert:x:108:
lpadmin:x:109:fred
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:fred
[B][COLOR=Red]pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:[/COLOR][/B]
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
fred:x:1000:
saned:x:124:
ntp:x:125:
vde2-net:x:126:
kvm:x:127:fred
Debian-exim:x:128:
```

---

### Post by ArtPulse on 2008-04-25
Am I lucky or what? xP lol pulse...

all right, so how do I create another user without logging in to any account?
(or... re-install?)

---

### Post by jakupl on 2008-04-25
i would.

---

### Post by ArtPulse on 2008-04-25
Say no more

(actually, i'm answering from the LiveCD and installing right now xP)

user artpulse will do =) thank you guys!

Geez, I still am amazed how people know such details =) or where to look after xP, to solve problems you know... =P long way to learn =)

---

### Post by chrisccoulson on 2008-04-25
Boot in to recovery mode (select the option when GRUB loads before the Ubuntu splash screen). From there:
```
useradd -m <*user_name*>
passwd <*user_name*>
```

Will create the new user, their home dir and set the password

---

### Post by jakupl on 2008-04-25
yeah X) I find it quite amazing that Distro Jockey knew that by heart... funny stuff ;)

---

