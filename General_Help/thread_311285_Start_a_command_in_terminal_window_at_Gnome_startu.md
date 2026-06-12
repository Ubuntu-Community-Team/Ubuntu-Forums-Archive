---
title: "Start a command in terminal window at Gnome startup?"
date: 2006-12-02
forum: General Help
---

### Post by wammin on 2006-12-02
How do I configure Gnome session startup to launch a command in the terminal window at startup? I have an encrypted partition on my drive using TrueCrypt, and I want to have a terminal window come up and ask me for the passphrase as soon as I log in.

The command that I use to launch TrueCrypt and decrypt my partition is:
```
truecrypt /dev/sda5 /data --mount-options 'umask=000,uid=1000,gid=100'
```

I tried adding this to the Gnome session startup list, but it didn't seem to do anything. Any help?

---

### Post by nixclusive on 2006-12-02
Maybe adding ```
xterm <command>
``` to the startup script should help.

---

### Post by wammin on 2006-12-02
xterm didn't quite work, but it prompted me to do figure it out. This command did what I wanted:

```
gnome-terminal -x truecrypt /dev/sda5 /data --mount-options 'umask=000,uid=1000,gid=100'
```

---

### Post by reclusivemonkey on 2006-12-03
> **wammin said:**
> xterm didn't quite work, but it prompted me to do figure it out. This command did what I wanted:

```
gnome-terminal -x truecrypt /dev/sda5 /data --mount-options 'umask=000,uid=1000,gid=100'
```

If you want something to start only when opening a terminal, you can add the line to ~/.bashrc.

---

