---
title: "gnome-terminal fails in X11 forwarding when started by SSH"
date: 2015-06-24
forum: General Help
---

### Post by odror on 2015-06-24
Hi

If I start gnome-terminal in a remote machine as follows:

```
ssh -Y remote.machine "gnome-terminal" &
```

Then when trying to spawn a new window from the newly started gnome-terminal (for example xterm)
I get the following error:
```
xterm: Xt error: Can't open display: localhost:11.0
```

This does not happen if I ssh to the remote machine and then start gnome-terminal.
It also does not happen
if I type:
```
ssh -Y remote.machine "xterm" &
```

On the other hand
```
ssh -Y remote.machine "xterm -e gnome-terminal" &
```
fails

Any ideas why gnome-terminal fails to pass X11 credentials when started by ssh.

---

### Post by tgalati4 on 2015-06-25
Is it credentials or simply environment values that are not getting passed?  Run *env* in each case and compare the differences.  Even post them.

*Xterm* was written before man could count, so it's possible that it does not understand how to operate in a modern desktop environment, such as gnome.  I remember using xterm in 1983 on DEC workstations running Unix, so I know that it is older than dirt.

---

### Post by odror on 2015-06-25
> **tgalati4 said:**
> Is it credentials or simply environment values that are not getting passed?  Run *env* in each case and compare the differences.  Even post them.

*Xterm* was written before man could count, so it's possible that it does not understand how to operate in a modern desktop environment, such as gnome.  I remember using xterm in 1983 on DEC workstations running Unix, so I know that it is older than dirt.

diff env1 env2:
env1 is direct ssh (ssh 192.168.0.8)
env2 is ssh 192.168.0.8 "gnome-terminal"
```
1,2c1
< XDG_SESSION_ID=1635
< TERM=xterm-256color
---
> XDG_SESSION_ID=1634
4,7c3,7
< XDG_SESSION_COOKIE=f18daf13a93434b5881b0a22535163aa-1435241294.273132-324478225
< SSH_CLIENT=192.168.0.8 50564 22
< __GL_SYNC_DISPLAY_DEVICE=HDMI-0
< SSH_TTY=/dev/pts/18
---
> VTE_VERSION=3803
> TERM=xterm
> XDG_SESSION_COOKIE=f18daf13a93434b5881b0a22535163aa-1435241268.933094-815523474
> SSH_CLIENT=192.168.0.8 50546 22
> WINDOWID=44040199
10c10
< LIBVIRT_DEFAULT_URI=qemu:///system
---
> PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
12,13d11
< PATH=/home/dror/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
< QT_QPA_PLATFORMTHEME=appmenu-qt5
16c14
< SHLVL=1
---
> SHLVL=2
19c17
< SSH_CONNECTION=192.168.0.8 50564 192.168.0.3 22
---
> SSH_CONNECTION=192.168.0.8 50546 192.168.0.3 22
21d18
< XDG_RUNTIME_DIR=/run/user/1000
22a20
> XDG_RUNTIME_DIR=/run/user/1000
```

---

