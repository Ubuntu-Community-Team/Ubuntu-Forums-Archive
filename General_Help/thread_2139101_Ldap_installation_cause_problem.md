---
title: "Ldap installation cause problem"
date: 2013-04-26
forum: General Help
---

### Post by Rakeshvijayan on 2013-04-26
I use Ryaz khan site to install ldap . [http://ryaz.homeip.net/?show=howtos](http://ryaz.homeip.net/?show=howtos)

By his instruction "Now let test our ldap authentication 
ssh rkhan@localhost"

Result is like this 
> sudo ssh rkhan@localhost
rkhan@localhost's password: 
Permission denied, please try again.
rkhan@localhost's password: 
Connection closed by UNKNOWN
hate@ldap:~$ sudo ssh rkhan@127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
ECDSA key fingerprint is ff:df:35:0d:00:3e:95:5f:6c:6d:ce:a2:89:a2:ee:b8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '127.0.0.1' (ECDSA) to the list of known hosts.
rkhan@127.0.0.1's password: 
Permission denied, please try again.
rkhan@127.0.0.1's password: 




I am not able to login in local system with rkhan but I can login with other user  I use his name and password for testing ..Please suggest if any one know about the problem please help me

---

### Post by Rakeshvijayan on 2013-04-26
when I tried to search the user it not showing the rhan user and group ,do I need to create home directory for the user manualy 
> 
hate@ldap:~$ cat /etc/group
root:0:
daemon:1:
bin:2:
sys:3:
adm:4:hate
tty:5:
disk:6:
lp:7:
mail:8:
news:9:
uucp:10:
man:12:
proxy:13:
kmem:15:
dialout:20:
fax:21:
voice:22:
cdrom:24:hate
floppy:25:
tape:26:
sudo:27:hate
audio:29ulse
dip:30:hate
www-data:33:
backup:34:
operator:37:
list:38:
irc:39:
src:40:
gnats:41:
shadow:42:
utmp:43:
video:44:
sasl:45:
plugdev:46:hate
staff:50:
games:60:
users:100:
nogroup:65534:
libuuid:101:
crontab:102:
syslog:103:
fuse:104:
messagebus:105:
bluetooth:106:
scanner:107:
colord:108:
lpadmin:109:hate
ssl-cert:110:
lightdm:111:
nopasswdlogin:112:
netdev:113:
whoopsie:114:
mlocate115:
ssh116:
avahi-autoipd:117:
avahi118:
pulse:119:
pulse-access:120:
utempter:121:
rtkit:122:
saned:123:
hate:1000:
sambashare:124:hate
mysql:125:
bind:126:
openldap:127:
hate@ldap:~$ id rkhan
uid=10000(rkhan) gid=10000 groups=10000
hate@ldap:~$ egrep -i "^rkhan" /etc/passwd
hate@ldap:~$ 



---

