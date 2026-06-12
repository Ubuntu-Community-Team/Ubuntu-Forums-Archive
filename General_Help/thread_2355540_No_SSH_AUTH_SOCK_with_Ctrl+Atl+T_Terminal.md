---
title: "No SSH_AUTH_SOCK with Ctrl+Atl+T Terminal"
date: 2017-03-13
forum: General Help
---

### Post by rogertawa on 2017-03-13
Hi all,

When I press CTRL+ALT+T to open a terminal, I am missing SSH envrionment variables.  However, when open a terminal by pressing the Windows key, searching for terminal and running it, I have them.  More specifically, I am missing the following variables:

[LIST]
[*]GNOME_SESSION_XDG_SESSION_PATH
[*]SSH_AGENT_LAUNCHER
[*]SSH_AUTH_SOCK
[*]COMPIZ_BIN_PATH
[/LIST]

whereas the following variables exist but have different values (which seems normal):

[LIST]
[*]WINDOWID
[*]GTK_MODULES
[*]JOURNAL_STREAM
[/LIST]

I am using Ubutnu 16.10 yakkety:

```
rogerta@argon:~$ uname -a
Linux argon 4.8.0-41-generic #44-Ubuntu SMP Fri Mar 3 15:27:17 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

rogerta@argon:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.10
DISTRIB_CODENAME=yakkety
DISTRIB_DESCRIPTION="Ubuntu 16.10"
```

with the Unity desktop.  One change I made to the default environment: I turned off the gnome-keyring because it does not work with ed25519 keys.  I turned it off by copying /etc/xdg/autostart/gnome-keyring-ssh.desktop to ~/.config/autostart/ and adding one line:

```
rogerta@argon:~$ diff /etc/xdg/autostart/gnome-keyring-ssh.desktop ~/.config/autostart/gnome-keyring-ssh.desktop 
6a7
> X-GNOME-Autostart-enabled=false
```

I'd really like to have the variables defined in the CTRL+ALT+T terminal.  I did not finding anything in these forums or by googling.  Any help greatly appreciated.

Thanks,
Roger

---

### Post by rogertawa on 2017-03-14
As a workaround, if Terminal is locked to the launcher, then pressing "Super + Shift + <num>" will open a new terminal window that has the SSH environment variables.  <num> depends on the position where the Terminal icon is locked to the launcher.  To find the number, just press and hold down Super and wait for the number to appear over the Terminal icon.

---

