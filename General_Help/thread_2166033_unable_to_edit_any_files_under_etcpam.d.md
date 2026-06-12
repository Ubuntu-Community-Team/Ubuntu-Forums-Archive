---
title: "unable to edit any files under /etc/pam.d/"
date: 2013-08-07
forum: General Help
---

### Post by rabin-banerjee91 on 2013-08-07
[COLOR=#333333][FONT=lucida grande]unable to edit any files under /etc/pam.d/,....any suggestion ??[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]drwxr-xr-x 2 root root 4096 Sep 25 2012 pam.d[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]# chmod 777 /etc/pam.d/[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]chmod: changing permissions of `/etc/pam.d/': Operation not permitted[/FONT][/COLOR]

[COLOR=#333333][FONT=lucida grande]??????????[/FONT][/COLOR]

---

### Post by deadflowr on 2013-08-07
I don't recommend changing permissions on system files.
But that being stated,
you can try
```
chmod -R 777 /etc/pam.d/
```
The -R option will change the permission recursively in the directory.

---

### Post by rabin-banerjee91 on 2013-08-07
no luck!!!!
#chmod -R 777 /etc/pam.d/
chmod: changing permissions of `/etc/pam.d/': Operation not permitted
chmod: changing permissions of `/etc/pam.d/gnome-screensaver': Operation not permitted
chmod: changing permissions of `/etc/pam.d/cups': Operation not permitted
chmod: changing permissions of `/etc/pam.d/samba': Operation not permitted
chmod: changing permissions of `/etc/pam.d/chsh': Operation not permitted
chmod: changing permissions of `/etc/pam.d/login': Operation not permitted
chmod: changing permissions of `/etc/pam.d/sudo': Operation not permitted
chmod: changing permissions of `/etc/pam.d/su': Operation not permitted
chmod: changing permissions of `/etc/pam.d/common-session': Operation not permitted
chmod: changing permissions of `/etc/pam.d/chpasswd': Operation not permitted
chmod: changing permissions of `/etc/pam.d/newusers': Operation not permitted
chmod: changing permissions of `/etc/pam.d/polkit-1': Operation not permitted
chmod: changing permissions of `/etc/pam.d/common-password': Operation not permitted
chmod: changing permissions of `/etc/pam.d/cron': Operation not permitted
chmod: changing permissions of `/etc/pam.d/sshd': Operation not permitted
chmod: changing permissions of `/etc/pam.d/atd': Operation not permitted
chmod: changing permissions of `/etc/pam.d/common-account': Operation not permitted
chmod: changing permissions of `/etc/pam.d/chfn': Operation not permitted
chmod: changing permissions of `/etc/pam.d/passwd': Operation not permitted
chmod: changing permissions of `/etc/pam.d/common-auth': Operation not permitted
chmod: changing permissions of `/etc/pam.d/other': Operation not permitted
chmod: changing permissions of `/etc/pam.d/lightdm': Operation not permitted
chmod: changing permissions of `/etc/pam.d/common-session-noninteractive': Operation not permitted
chmod: changing permissions of `/etc/pam.d/lightdm-autologin': Operation not permitted
chmod: changing permissions of `/etc/pam.d/ppp': Operation not permitted
chmod: changing permissions of `/etc/pam.d/nvuauth': Operation not permitted

---

### Post by rabin-banerjee91 on 2013-08-07
any suggestion ???

---

### Post by CitadelUniversal on 2013-08-07
Are you using root or normal user in the terminal? If using root you should be able to change permissions.

---

### Post by rabin-banerjee91 on 2013-08-07
using root user..

---

### Post by rabin-banerjee91 on 2013-08-07
root@XXXXXXXX:/etc# chmod -R 777 pam.d/
chmod: changing permissions of `pam.d/': Operation not permitted
chmod: changing permissions of `pam.d/gnome-screensaver': Operation not permitted
chmod: changing permissions of `pam.d/cups': Operation not permitted
chmod: changing permissions of `pam.d/samba': Operation not permitted
chmod: changing permissions of `pam.d/chsh': Operation not permitted
chmod: changing permissions of `pam.d/login': Operation not permitted
chmod: changing permissions of `pam.d/sudo': Operation not permitted
chmod: changing permissions of `pam.d/su': Operation not permitted
chmod: changing permissions of `pam.d/common-session': Operation not permitted
chmod: changing permissions of `pam.d/chpasswd': Operation not permitted
chmod: changing permissions of `pam.d/newusers': Operation not permitted
chmod: changing permissions of `pam.d/polkit-1': Operation not permitted
chmod: changing permissions of `pam.d/common-password': Operation not permitted
chmod: changing permissions of `pam.d/cron': Operation not permitted
chmod: changing permissions of `pam.d/sshd': Operation not permitted
chmod: changing permissions of `pam.d/atd': Operation not permitted
chmod: changing permissions of `pam.d/common-account': Operation not permitted
chmod: changing permissions of `pam.d/chfn': Operation not permitted
chmod: changing permissions of `pam.d/passwd': Operation not permitted
chmod: changing permissions of `pam.d/common-auth': Operation not permitted
chmod: changing permissions of `pam.d/other': Operation not permitted
chmod: changing permissions of `pam.d/lightdm': Operation not permitted
chmod: changing permissions of `pam.d/common-session-noninteractive': Operation not permitted
chmod: changing permissions of `pam.d/lightdm-autologin': Operation not permitted
chmod: changing permissions of `pam.d/ppp': Operation not permitted
chmod: changing permissions of `pam.d/nvuauth': Operation not permitted

---

### Post by bapoumba on 2013-08-07
Why are you trying to do that ?```
~$ ls -la /etc/pam.d/gnome-screensaver 
-rw-r--r-- 1 root root 56 sept. 25  2012 /etc/pam.d/gnome-screensaver

```

---

### Post by rabin-banerjee91 on 2013-08-08
> **bapoumba said:**
> Why are you trying to do that ?```
~$ ls -la /etc/pam.d/gnome-screensaver 
-rw-r--r-- 1 root root 56 sept. 25  2012 /etc/pam.d/gnome-screensaver

```

because though permission is read-write but still i am not able to edit any files,.. :(

---

### Post by steeldriver on 2013-08-08
"operation not permitted" is different from "permission denied" - it often means that the file's immutable attribute has been set - you can check with lsattr e.g.

```
lsattr /etc/pam.d/gnome-screensaver
```

See the chattr man page (man chattr) for details

---

### Post by rabin-banerjee91 on 2013-08-08
> **steeldriver said:**
> "operation not permitted" is different from "permission denied" - it often means that the file's immutable attribute has been set - you can check with lsattr e.g.

```
lsattr /etc/pam.d/gnome-screensaver
```

See the chattr man page (man chattr) for details


Thanks man,....got it ,...!!!! ;)

---

