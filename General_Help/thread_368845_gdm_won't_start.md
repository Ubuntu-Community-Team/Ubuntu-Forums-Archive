---
title: "gdm won't start"
date: 2007-02-23
forum: General Help
---

### Post by duffer on 2007-02-23
Hi, I'm not sure if this is a Gnome desktop question or an Xserver question. I was setting up mambo on my PC. All went well, but then my gnome session went into hibernation on its own and I have been unable to start another desktop session. I logged on in recovery mode and copied this xsession-errors file. 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: 
running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l 
":0" "duffer"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

Does anyone know if reconfigure my xserver or if is something in the gnome setup.

Cheers,

Duffer

---

### Post by taurus on 2007-02-23
What's the output of this command from a prompt?

```
ls -la /home
```

---

### Post by duffer on 2007-02-23
well if I issue the command

ls -la /home

I get

.
..
duffer

---

### Post by taurus on 2007-02-23
The output should display a bunch of stuff, permissions and whatnot.  I just want to make sure you you are still the owner of your own $HOME directory so you can write to it when you log in.

---

### Post by ~LoKe on 2007-02-23
> **taurus said:**
> The output should display a bunch of stuff, permissions and whatnot.  I just want to make sure you you are still the owner of your own $HOME directory so you can write to it when you log in.

GDM should still come up even without a home directory.

---

### Post by duffer on 2007-02-23
yea sorry here are the permissions at /home

total 16
 drwxr-xr-x  4 root     root     4096 Feb  5 22:20 


. .drwxr-xr-x 21 root      root     4096 Feb 23 20:34 ..
   drwxr-xr-x 23 duffer   duffer   4096 Feb 23 19:31 duffer
   drwxr-xr-x 14 webadmin webadmin 4096 Feb 23 19:24 webadmin

---

### Post by k84 on 2007-02-25
Hi, I just got the same error because I did a check of the filesystem and somehow it changed the permissions in the /tmp folder and noone but root can write to it. Just change the permissions of the /tmp folder so you can write to it chmod a+w /tmp.

---

