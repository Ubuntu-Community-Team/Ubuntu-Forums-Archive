---
title: "groups: cannot find name for group [number]"
date: 2014-07-12
forum: General Help
---

### Post by Tristan_Williams on 2014-07-12
Every terminal I open gives this message:
```

groups: cannot find name for group ID 127

```

Running the command "groups" also gives that message



This started right after I uninstalled the following packages:
[LIST]
[*]0ad
[*]synfigstudio
[*]chromium-browser
[*]tor-browser
[*]wireshark
[*]cairo-dock
[/LIST]


So I think it probably has something to do with one of those packages.
Thanks for any help

---

### Post by deadflowr on 2014-07-12
```
getent group
```
will list all the groups, from /etc/group.
It'll also list the gid.
Should list them in numerical order.
See what shows up...

---

### Post by capscrew on 2014-07-12
> **Tristan_Williams said:**
> Every terminal I open gives this message:
```

groups: cannot find name for group ID 127

```

Running the command "groups" also gives that message



This started right after I uninstalled the following packages:
[LIST]
[*]0ad
[*]synfigstudio
[*]chromium-browser
[*]tor-browser
[*]wireshark
[*]cairo-dock
[/LIST]


So I think it probably has something to do with one of those packages.
Thanks for any help
The group number (gid) is not always the same from system to system.  To see what groups are available on the system use this command```
getent group
```  To list the 127 group you can use this```
getent group 127
```
Is there a group on your system with the gid=127 ?  There is no gid=127 on the system I am using right now.

---

### Post by Tristan_Williams on 2014-07-12
Nothing is shown for group 127:
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:tristan,bobtownca,syslog
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:tristan,bobtownca
fax:x:21:tristan,bobtownca
voice:x:22:
cdrom:x:24:tristan,bobtownca
floppy:x:25:tristan,bobtownca
tape:x:26:tristan,bobtownca
sudo:x:27:tristan,bobtownca
audio:x:29:pulse,tristan
dip:x:30:tristan,bobtownca
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:tristan,bobtownca
sasl:x:45:
plugdev:x:46:tristan,bobtownca
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
crontab:x:102:
syslog:x:103:
fuse:x:104:tristan,bobtownca
messagebus:x:105:
ssl-cert:x:106:
netdev:x:107:tristan
mlocate:x:108:
ssh:x:109:
utempter:x:110:
avahi-autoipd:x:111:
lpadmin:x:112:tristan
rtkit:x:113:
whoopsie:x:114:
bluetooth:x:115:
avahi:x:116:
lightdm:x:117:
nopasswdlogin:x:118:
pulse:x:119:
pulse-access:x:120:
scanner:x:121:saned,tristan
colord:x:122:
saned:x:123:
tristan:x:1000:
sambashare:x:124:tristan
bobtownca:x:1001:
winbindd_priv:x:125:
debian-tor:x:126:
gdm:x:128:

```

But still, when I open a terminal, or run the "bash" command, it says "groups: cannot find name for group ID 127"

---

### Post by steeldriver on 2014-07-12
Is there something in your .bashrc file that it might be related to? you can run

```

diff /etc/skel/.bashrc ~/.bashrc

```

to see anything that's been added to your .bashrc since creation

---

### Post by Tristan_Williams on 2014-07-12
I've only added one thing to ~/.bashrc, which is my custom $PS1
That being said, 'diff /etc/skel/.bashrc ~/.bashrc' returns absolutely nothing

---

### Post by varunendra on 2014-07-13
Just for reference (won't be relevant or correct for all systems), the group id 127 in my system is of 'vboxusers' group. The entry in /etc/group is -
```
clamav:x:125:
debian-tor:x:126:
**vboxusers:x:127:varun**
dictd:x:128:
```

Watching the progress with curiosity.

---

### Post by Tristan_Williams on 2014-07-13
Well it suddenly doesn't do it today so I give up

---

### Post by bapoumba on 2014-07-13
Well, could be the right timing to see which group is 127..

---

### Post by Tristan_Williams on 2014-07-13
> **bapoumba said:**
> Well, could be the right timing to see which group is 127..

Still nothing

---

### Post by steeldriver on 2014-07-13
Did you log in to a guest account recently? it could have been the GID of a guest account that has since been deleted/cleaned up

---

### Post by Tristan_Williams on 2014-07-13
> **steeldriver said:**
> Did you log in to a guest account recently? it could have been the GID of a guest account that has since been deleted/cleaned up

No

I suspect that it was the "wireshark" group, because I just uninstalled wireshark. I hadn't rebooted yet when this problem started occurring, and now that I think of it, it only stopped after I rebooted.

---

### Post by fallenangel2 on 2014-12-19
I recently removed a system user and group and was left with the same 127 group error. i removed any .bash_aliases related to the group (it had been a deluge webui) and restarted ubuntu. the error from the terminal was removed and when i reran groups the error was removed. try restart.

---

