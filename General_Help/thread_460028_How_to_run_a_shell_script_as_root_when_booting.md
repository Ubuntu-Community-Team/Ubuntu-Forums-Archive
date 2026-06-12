---
title: "How to run a shell script as root when booting?"
date: 2007-05-31
forum: General Help
---

### Post by loathsome on 2007-05-31
Hi there,

I've created a nifty script that does some stuff with my web cam, but it needs root privileges. How do I do it so it starts when I boot / log in to GNOME? I know I can use «gksudo», but that's .. too much work for me to type in every single time I boot up. Heh.

Thanks!

---

### Post by regomodo on 2007-05-31
Are you looking for how to have an autostarted script?

Preferences/Sessions/New

---

### Post by dbott67 on 2007-05-31
I'm not sure if it will work for you, but you can include scripts (or links to scripts) in the **/etc/rc3.d** folder.

For example, the [COLOR=Blue]DenyHosts[/COLOR] script which checks log files for SSH attacks requires that the user create a link to the denyhosts script in **/etc/init.d/**:
```
dbott@feisty:/etc/rc3.d$ ls -al
total 20
drwxr-xr-x   2 root root  4096 2007-05-21 16:28 .
drwxr-xr-x 122 root root 12288 2007-05-31 08:46 ..
-rw-r--r--   1 root root   556 2007-04-10 17:46 README
lrwxrwxrwx   1 root root    17 2007-04-22 15:04 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root    15 2007-04-22 14:52 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root    18 2007-04-22 14:51 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root    34 2007-04-22 14:54 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root    15 2007-04-22 14:51 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root    14 2007-04-22 15:03 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root    13 2007-04-22 15:08 S13gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    16 2007-04-22 15:06 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root    15 2007-04-22 15:06 S19hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root    14 2007-04-22 15:04 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root    16 2007-04-22 15:04 S20apport -> ../init.d/apport
[COLOR=Blue] l[/COLOR][COLOR=Blue]rwxrwxrwx   1 root root    19 2007-05-21 16:28 S20denyhosts -> ../init.d/denyhosts[/COLOR]
lrwxrwxrwx   1 root root    22 2007-04-22 15:05 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root    17 2007-04-22 14:50 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root    23 2007-04-22 14:52 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root    19 2007-04-22 15:05 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root    15 2007-04-22 15:04 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2007-04-26 11:39 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    13 2007-04-22 16:06 S20ssh -> ../init.d/ssh
lrwxrwxrwx   1 root root    17 2007-04-26 11:36 S20winbind -> ../init.d/winbind
lrwxrwxrwx   1 root root    19 2007-04-22 15:05 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    17 2007-04-22 15:04 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2007-04-22 15:04 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2007-04-22 15:04 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    24 2007-04-22 15:04 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    17 2007-04-28 15:43 S91apache2 -> ../init.d/apache2
lrwxrwxrwx   1 root root    17 2007-04-22 15:06 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2007-04-22 15:04 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    18 2007-04-22 21:09 S99nxsensor -> ../init.d/nxsensor
lrwxrwxrwx   1 root root    18 2007-04-22 21:10 S99nxserver -> ../init.d/nxserver
lrwxrwxrwx   1 root root    18 2007-04-22 14:51 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2007-04-22 14:51 S99rmnologin -> ../init.d/rmnologin

```So, you could do the same:

1. Switch to root:
```
sudo su
```2. Make a link to the script file in **/etc/rcd.3** (call it something like [COLOR=Red]**S50NameOfScript**[/COLOR]).  The 'S' means 'start' (whereas 'K' would be 'kill') and the number allows the services/scripts to run in some sort of preferential order.

-Dave

---

### Post by loathsome on 2007-05-31
> **regomodo said:**
> Are you looking for how to have an autostarted script?

Preferences/Sessions/New

Did you read my post? I want it to run as **ROOT** without using gksudo.

---

### Post by yota on 2007-05-31
Hi,

put a call to your script in '/etc/rc.local', it's meant exactly to execute commands at boot time as root, just take care to leave 'exit 0' on the end.

Hope this helps!

---

