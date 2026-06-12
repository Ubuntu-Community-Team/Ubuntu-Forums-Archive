---
title: "problems with terminal"
date: 2013-09-20
forum: General Help
---

### Post by mreyna16 on 2013-09-20
im trying to build an android rom, and when i do a repo sync it exits out randomly from terminal and i thought to myself, it must be a problem with the repo. so after trying three or four times i came to the conclusion that its not the repo, its the terminal thats not working well. the reason i think its the terminal is because even before doing a sync, just by navigating to any folder it closes out. any help as to figure out whats causing this?

---

### Post by mreyna16 on 2013-09-20
> **mreyna16 said:**
> im trying to build an android rom, and when i do a repo sync it exits out randomly from terminal and i thought to myself, it must be a problem with the repo. so after trying three or four times i came to the conclusion that its not the repo, its the terminal thats not working well. the reason i think its the terminal is because even before doing a sync, just by navigating to any folder it closes out. any help as to figure out whats causing this?
anybody?

---

### Post by steeldriver on 2013-09-20
Well if gnome-terminal is crashing the first place I'd check is ~/.xsession-errors

---

### Post by mreyna16 on 2013-09-20
> **steeldriver said:**
> Well if gnome-terminal is crashing the first place I'd check is ~/.xsession-errors
this is what i see:

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by mreyna16 on 2013-09-21
so im trying to make an android rom (was able to compile last week) but now my terminal closes out when i do a repo sync. i go to the .xsession-errors file and open it and this is the error i see for nautilus...

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

ive tried re-installing nautilus, removing it and installing it, even installing nautilus-share but still closes out

---

### Post by Jonathan Precise on 2013-09-21
That error is normal for nautilus if run as root (or with "sudo", not "gksu").

As for errors that appear, post with code tags:

[noparse]```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error: No such file or directory.
Please ask your system administrator to enable user sharing.
```[/noparse]

To make:

```
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error: No such file or directory.
Please ask your system administrator to enable user sharing.
```

---

### Post by mreyna16 on 2013-09-21
so then how can i figure out why the terminal closes? it didnt do that before

---

### Post by Old_Grey_Wolf on 2013-09-21
Threads merged.

---

### Post by steeldriver on 2013-09-21
By "repo sync" do you just mean 'sudo apt-get update'? if so I can't think why that would crash the terminal, but here are a couple of things you could try:

[LIST]
[*]starting a plain xterm and issuing the 'apt-get update' in that (in case it's a problem with gnome-terminal specifically) 
[*]switching to a virtual terminal (Ctrl-Alt-F1 thru F6) and trying the update there 
[/LIST]

---

