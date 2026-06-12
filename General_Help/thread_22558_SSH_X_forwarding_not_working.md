---
title: "SSH X forwarding not working"
date: 2005-03-28
forum: General Help
---

### Post by agenkin on 2005-03-28
On an up-to-date installation of Hoary, I cannot use SSH X forwarding.  Wenever I do, for instance, "ssh -X localhost" (or any other host, for that matter) and then try to launch a simple X program (for example, xterm), I get the following error message:

X11 connection rejected because of wrong authentication.
X connection to localhost:10.0 broken (explicit kill or server shutdown).

The X11 forwarding is enabled in the /etc/ssh/sshd_config:

X11Forwarding yes
X11DisplayOffset 10

I don't think it's relevant, but I am running the KDE desktop.

Any insight would be greately appreciated.

---

### Post by dataw0lf on 2005-03-28
Hm... what's your /etc/hosts.deny file look like?

---

### Post by agenkin on 2005-03-29
[QUOTE=dataw0lf]Hm... what's your /etc/hosts.deny file look like?[/QUOTE]

It's empty, and so is hosts.allow.

This is my first experince with X.org: perhaps it has some setting somewhere to enable networked connections (i.e. the ones not going through the Unix domain socket file)?

---

### Post by az on 2005-03-29
"don't think it's relevant, but I am running the KDE desktop"

Offhand, I know that gdm sets up the permissions for this sort of thing, but when I used to run KDM, I always had to do

xhosts +

in a terminal before I would be able to use another user's client application.

---

### Post by agenkin on 2005-03-29
FWIW I am using the vanilla 'xdm', not kdm or gdm.  In any case "xhost +" does not help in me: I still get the dreaded error message. :(

---

### Post by agenkin on 2005-03-29
I solved the problem.  It was my ~/.Xauthority file. "xauth list" reported some corrupt entries, so when I removed ~/.Xauthority, it got re-created properly, and now X forwarding works just like it used to.

---

### Post by hil on 2006-08-10
The same here; I solve the problem of "X11 connection rejected" by removing  .Xauthority at $HOME

Somehow my $HOME/.Xauthority had bad permission:[-X 
```
h@dance:~$ ls -Al $HOME/.Xauthority
-rw------- 1 root root 0 2006-08-09 22:01 .Xauthority
h@dance:~$ sudo rm $HOME/.Xauthority

```

Remove it and reconnect to the host using:razz: 
```
ssh -l h -X -Y 192.168.12.5 #Your host IP
```

It should belong to $USER, not root

I suppose the permission is changed by using 'sudo'. I also found that some .* files had root ownership.
Do an inspection to check if you have the correct permission at $HOME:cool: 
```

$ cd $HOME
$ ls -Al .* * |grep root
```

---

### Post by mirak63 on 2006-08-16
I needed to put x11forward yes in /etc/ssh/ssh_config
This allow connecting clients to do ssh forwarding.
I though it would be in sshd_config but it was already on yes.

---

### Post by mbradlcu on 2007-02-01
X11 forward was set to yes in /etc/ssh/sshd_conf but my ~/.Xauthority was 600/root, I changed the ownership to the home user but I still received the error.. I deleted and 'touch'ed ~/.Xauthority and now it works...

---

