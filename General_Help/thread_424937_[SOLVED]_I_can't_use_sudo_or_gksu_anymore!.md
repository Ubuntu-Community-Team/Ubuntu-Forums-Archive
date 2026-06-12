---
title: "[SOLVED] I can't use sudo or gksu anymore!"
date: 2007-04-27
forum: General Help
---

### Post by drakos on 2007-04-27
First time linux user here... so for some reason, I can no longer run any command that requires sudo or gksu. When I try to it says,  sudo: must be setuid root. I'm assuming this has something to do with my foolish tinkering with permissions, but even after going back and changing the permissions back to what I think there were originally I still can't get sudo to work (outside of logging in as root).

Here's what happens when I try to run synaptic

```
drakos@DrakosXfce:~$ gksudo --debug synaptic
No ask_pass set, using default!
xauth: /tmp/libgksu-gi6304/.Xauthority
STARTUP_ID: gksudo/synaptic/6109-0-DrakosXfce_TIME6328189
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: -sudo: must be setuid root-
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-gi6304/.Xauthority
xauth_env: /tmp/.gdm1RPMRT
dir: /tmp/libgksu-gi6304

```

I'm at a loss.

---

### Post by drakos on 2007-04-27
I found a thread that fixed this, so if you stumble upon this and have the same problem here is the solution that fixed it for me:

Log-in as root and enter this into the terminal.

```
chown root:root /usr/bin/sudo
chmod 4755 /usr/bin/sudo
```

Here's the thread for more info: [http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root]("http://ubuntuforums.org/showthread.php?t=228443&highlight=setuid+root")
Check out post #9.

---

