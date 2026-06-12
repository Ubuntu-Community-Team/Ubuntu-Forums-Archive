---
title: "'System problem detected' message for about 4 weeks now"
date: 2019-08-15
forum: General Help
---

### Post by MoebusNet on 2019-08-15
This is from my Lubuntu 18.04 32-bit machine.

I have no clue what to do about this; I don't use kwallet or gnome keyring. A Google search said to look at journalctl -

```
 journalctl -p 3 -b

Aug 15 11:28:21 Flying-Cloud kernel: sd 2:0:0:0: [sdb] No Caching mode page found
Aug 15 11:28:21 Flying-Cloud kernel: sd 2:0:0:0: [sdb] Assuming drive cache: write through
Aug 15 11:28:43 Flying-Cloud kernel: scsi 2:0:0:1: Failed to get diagnostic page 0x1
Aug 15 11:28:43 Flying-Cloud kernel: scsi 2:0:0:1: Failed to bind enclosure -19
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No 
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM adding faulty module: pam_gnome_keyring.so
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM adding faulty module: pam_kwallet.so
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file 
Aug 15 11:28:51 Flying-Cloud lightdm[580]: PAM adding faulty module: pam_kwallet5.so
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM unable to dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot open shared object file: No 
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM adding faulty module: pam_gnome_keyring.so
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM adding faulty module: pam_kwallet.so
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file 
Aug 15 11:28:56 Flying-Cloud lightdm[694]: PAM adding faulty module: pam_kwallet5.so

```

I would welcome suggestions.

---

### Post by #&amp;thj^% on 2019-08-15
The first command is probably not needed but for the proper (Safety) way, I always make sure to have a back-up.(When mucking about)
```

sudo cp -a /etc/pam.d /etc/pam.d_bak
sudo pam-auth-update --force
```

---

### Post by MoebusNet on 2019-08-15
Thanks! So this basically forces PAM module to update?

I also found this in /var/crash -
 ```
~$ ls -l /var/crash
total 596
-rw-r----- 1 root whoopsie 607705 Aug 15 10:40 _sbin_plymouthd.0.crash

```

---

### Post by #&amp;thj^% on 2019-08-15
Ah more to the story, what dose this produce:
```
apt policy plymouth-x11
``` 
And sometimes as easy as:
```
sudo chown -R $USER: /lib/plymouth
```

---

### Post by MoebusNet on 2019-08-15
```
~$ apt policy plymouth-x11
plymouth-x11:
  Installed: (none)
  Candidate: 0.9.3-1ubuntu7.18.04.2
  Version table:
     0.9.3-1ubuntu7.18.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
     0.9.3-1ubuntu7 500
        500 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages

```

---

### Post by #&amp;thj^% on 2019-08-15
See if installing it helps. ;)
Also I left this out:
A possible solution not mentioned yet is to run:
```

sudo dpkg-reconfigure Plymouth
```

---

### Post by MoebusNet on 2019-08-15
OK, I'll try restarting to see if the error message comes back. Thanks!

---

### Post by MoebusNet on 2019-08-15
I cleared /var/crash and no longer see the 'System problem detected' error message about plymouth on boot-up.

journalctl still has the same error messages about kwallet & gnome_keyring, but that doesn't seem to be triggering a 'System problem'  error message; maybe because kwallet & gnome_keyring are not installed (I haven't checked) or are unconfigure (I don't use them).

I think I'll call this SOLVED unless I start getting the error message again. Thanks for the help!

---

### Post by #&amp;thj^% on 2019-08-15
Yep I see other stuff related to my heavy tweaking systems:
```
Aug 15 07:45:57 arch systemd-udevd[310]: /etc/udev/rules.d/60-scheduler.rules:2: Invalid key/value pair, starting at character 66 (',')
Aug 15 07:45:57 arch systemd-udevd[310]: /etc/udev/rules.d/60-scheduler.rules:4: Invalid key/value pair, starting at character 69 (',')
Aug 15 07:45:57 arch systemd-udevd[310]: /etc/udev/rules.d/60-scheduler.rules:8: Invalid key/value pair, starting at character 69 (',')
Aug 15 07:45:57 arch systemd-udevd[407]: crypto_user: Failed to open ATTR{/sys/module/crypto_user/queue/scheduler} for writing: No such file or directory
Aug 15 07:45:57 arch systemd-udevd[407]: crypto_user: Failed to open ATTR{/sys/module/crypto_user/queue/scheduler} for writing: No such file or directory

```
Glad to hear the message went away though, <**Thanks for being the better part of UF.** :)>

---

