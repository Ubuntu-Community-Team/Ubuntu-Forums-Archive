---
title: "sudo not asking for password"
date: 2006-08-17
forum: General Help
---

### Post by AirRaven on 2006-08-17
Recently I've noticed that the sudo command's not been asking for my password. I actually can't remember when it started happening- all I know is that it's here now.

I've not had sudo, gksu, kdesu, or gksudo ask me for my password in a while. I don't mean the standard every-15-minutes pause- I mean it's literally never asking me for my password.

Does anyone have any suggestions to find out what's causing this? I'm not running on the root account. I've enabled the root account using [FONT="Courier New"]sudo passwd root[/FONT], but I've done that several times on other installs without this problem- I've only ever used it for the [FONT="Courier New"]su[/FONT] command.

---

### Post by aysiu on 2006-08-17
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

If you're still having this problem after changing /etc/group and /etc/sudoers back to their defaults... I'm stumped.

---

### Post by AirRaven on 2006-08-21
Okay. After having edited /etc/sudoers to the version you provided on your site, I've sort of messed things up.

I was silly enough to ignore the large "This file MUST be edited with the visudo command" text at the head of the file, so I edited it with a simple [FONT="Courier New"]sudo nano[/FONT]. 

The end result is this beauty:
```
stelhan@stelhan-desktop:~$ sudo nano
>>> sudoers file: syntax error, line 20 <<<
sudo: parse error in /etc/sudoers near line 20
```

These are the contents of my /etc/sudoers file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL)

```

---

### Post by aysiu on 2006-08-21
Line 20 in the tutorial says ```
%admin ALL=(ALL) ALL
``` But your line 20 says ```
%admin ALL=(ALL)
```

---

