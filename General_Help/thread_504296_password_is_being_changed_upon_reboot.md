---
title: "password is being changed upon reboot"
date: 2007-07-19
forum: General Help
---

### Post by liquidarts on 2007-07-19
I've been building a MythTV box for awhile and recently my password has been getting changed during reboot.  I'm running feisty with autologon enabled so I don't enter a password except for ssh'ing in and admin tasks.  I'm certain of what my password should be but that doesn't work.  I had to reboot into recovery mode from grub and using that root login to change my regular account's password.  I then finished booting and everything worked fine until the next reboot when it was changed again.

How can I track down what is happening during the boot process, ie what services are starting, or scripts etc... so I can start to find what's causing this?

The only things I've been working with recently was Amarok and mysql if that lends any clues!?

---

### Post by liquidarts on 2007-08-06
Anybody have any ideas... is there some way to log what's happening during bootup, or disable startup items to see if it stops getting changed?

---

### Post by nitro_n2o on 2007-08-06
press ALT+F2 when you see the loading bar this should show you a verbose mode.. 
and it's all stored in /var/log/boostrap.log

---

### Post by liquidarts on 2007-08-08
It's a pretty full file, can I delete it and reboot so it's fresh?
In my bootstrap.log file I see these;

```
Setting up sudo (1.6.8p12-4ubuntu5) ...
No /etc/sudoers found... creating one for you.
```


```
Setting up gnupg (1.4.6-1ubuntu2) ...
Setting up ubuntu-keyring (2005.01.12.1) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: /etc/apt/trustdb.gpg: trustdb created
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 2
gpg:               imported: 1
gpg:              unchanged: 1
gpg: no ultimately trusted keys found
gpg: keyring `/usr/share/keyrings/ubuntu-archive-removed-keys.gpg' created
```

Any thoughts if they are an issue.

---

