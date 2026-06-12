---
title: "Lost /etc/group, need it from fresh install"
date: 2008-05-23
forum: General Help
---

### Post by n0_mad on 2008-05-23
Hi All.
I have following problem:
I deleted myself from all groups due to wrong use of usermod.
Then i reboted to recovery mode and added myself manually to needed groups. All works fine again, but users-admin(gnome applet to manage users) was not display groups at all, but file /etc/group was ok. I decided to add some groups and look what will happen. I clicked add new group, tiped test, click ok then i discovered my /etc/group was rewrited by user-admin with only one group: test. 
So my system got unusable. I booted from livecd and copy content of /etc/grop to my broken /etc/group, and replaced user ubuntu to myself. After reboot system work, but things broken: cant mount disks thru places, cant open user-admin, cant start network monitor applet.

Could you please post /etc/group from fresh ubuntu 8.04 installation?
I dont want to do fresh install because i have just updated all packages etc. Problem just in /etc/group

---

### Post by sdennie on 2008-05-23
From a fresh Hardy VM install:

```

$ cat /etc/group | sed -e s/my_username/your_username/
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:your_username
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:your_username
fax:x:21:
voice:x:22:
cdrom:x:24:your_username
floppy:x:25:your_username
tape:x:26:
sudo:x:27:
audio:x:29:pulse,your_username
dip:x:30:your_username
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:your_username
sasl:x:45:
plugdev:x:46:your_username
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
fuse:x:107:your_username
ssl-cert:x:108:
lpadmin:x:109:your_username
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:your_username
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
your_username:x:1000:

```

Change "your_username" to your login name.  Permissions are:

```

-rw-r--r-- 1 root root 889 2008-05-08 20:12 /etc/group

```

Hope that helps.

---

### Post by n0_mad on 2008-05-23
Thank you. Used it but no change, still have problems with gnome security tools.

Got this if i try start them from console
```

nomad@box:/etc$ users-admin 

** (users-admin:7546): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

nomad@box:/etc$ network-admin 

(network-admin:7551): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7551): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

```
If i try star them from menu i got message "The configuration could not be loaded.You are not allowed to access the system configuration. "

---

### Post by mali2297 on 2008-05-23
Post the output of
```

cat /etc/group /etc/passwd | grep messagebus

```

---

### Post by n0_mad on 2008-05-23
Here it is
```

nomad@box:/etc$ cat /etc/group /etc/passwd | grep messagebus
messagebus:x:119:nomad
messagebus:x:108:65534::/var/run/dbus:/bin/false

```

---

### Post by mali2297 on 2008-05-23
> **n0_mad said:**
> Here it is
```

nomad@box:/etc$ cat /etc/group /etc/passwd | grep messagebus
messagebus:x:119:nomad
messagebus:x:108:65534::/var/run/dbus:/bin/false

```

The second line looks somewhat strange to me. Try recreating the user *messagebus* with
```

sudo userdel messagebus
sudo useradd -u 119 -g messagebus -d /var/run/dbus -s /bin/false messagebus
sudo passwd -l messagebus
sudo chown -R messagebus:messagebus /var/run/dbus

```
Then reboot.

---

### Post by n0_mad on 2008-05-23
Thanks for helping but i just reinstaled system=)

---

