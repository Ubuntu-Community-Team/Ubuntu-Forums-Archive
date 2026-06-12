---
title: "ssh daemon not started"
date: 2008-07-05
forum: General Help
---

### Post by xaenyx on 2008-07-05
OK, I am stumped.  I just installed ubuntu on this computer that I want to make into a media server, but I can't get ssh to work.  

```

user@user-desktop:/var/log$ ssh user@localhost
ssh: connect to host localhost port 22: Connection refused

```

In fact, the ssh daemon isn't started:

```

user@user-desktop:/var/log$ netstat -an | grep "LISTEN "
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
user@user-desktop:/var/log$ ps aux|grep ssh
user     15360  0.0  0.3   3004   768 pts/0    S+   23:35   0:00 grep ssh

```

And I don't see a way to install it:

```

user@user-desktop:/var/log$ sudo apt-cache search ssh
[sudo] password for user: 
seahorse - A Gnome front end for GnuPG
libssl0.9.8 - SSL shared libraries
libndesk-dbus1.0-cil - CLI implementation of D-Bus
ssh-askpass-gnome - interactive X program to prompt users for a passphrase for ssh-add
x11-session-utils - X session utilities
gnome-keyring - GNOME keyring services (daemon and tools)
libpam-gnome-keyring - PAM module to unlock the GNOME keyring upon login
libndesk-dbus-glib1.0-cil - CLI implementation of D-Bus (GLib mainloop integration)
libgnome-keyring0 - GNOME keyring services library
openssh-client - secure shell client, an rlogin/rsh/rcp replacement

```

help?

---

### Post by coolaj86 on 2008-07-05
Only the client is installed by default.

```
sudo apt-get install ssh # Install the server
sudo ufw enable # start the firewall
sudo ufw allow ssh # allow ssh
sudo apt-get install fail2ban # protect yourself from ssh attacks that happen all day long
```

---

### Post by xaenyx on 2008-07-05
> **coolaj86 said:**
> Only the client is installed by default.

```
sudo apt-get install ssh # Install the server
sudo ufw enable # start the firewall
sudo ufw allow ssh # allow ssh
sudo apt-get install fail2ban # protect yourself from ssh attacks that happen all day long
```

The ssh package is, I think, the same as openssh-client, which I already have installed.  The problem is that openssh-server appears to not be installed.  (and installing ssh anyway doesn't work)

```

user@user-desktop:/var/log$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate

user@user-desktop:/var/log$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate

```

---

### Post by ghostdog74 on 2008-07-05
what is the output when you run this
```
find /etc/ -type f -name "*ssh*"

```

---

### Post by xaenyx on 2008-07-05
```

user@user-desktop:/var/log$ sudo find /etc/ -type f -name "*ssh*"
/etc/X11/Xsession.d/90x11-common_ssh-agent
/etc/ssh/ssh_config

```

---

### Post by coolaj86 on 2008-07-05
> This may mean that the package is missing, has been obsoleted, or
is only available from another source


it seems that your apt-get sources have become corrupted or something weird.

how about this:
```
sudo apt-get update
```

And check in System > Admin > Software Sources
and make sure that things look right in there (most lines except the ones that say 'source' are checked)

---

### Post by coolaj86 on 2008-07-05
See if your output of the following command is similar to mine

```
cat /etc/apt/sources.list | grep -v '#'

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse


deb http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://dl.google.com/linux/deb/ stable non-free

```

---

### Post by ghostdog74 on 2008-07-05
> **xaenyx said:**
> ```

user@user-desktop:/var/log$ sudo find /etc/ -type f -name "*ssh*"
/etc/X11/Xsession.d/90x11-common_ssh-agent
/etc/ssh/ssh_config

```

you should have some sort of startup script like  /etc/init.d/sshd . A reinstall might do you good as someone have suggested.

---

### Post by xaenyx on 2008-07-05
Yep, it was a problem with apt-get, thanks.

---

