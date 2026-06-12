---
title: "Samba private auto-mounted share breaks constantly"
date: 2013-05-16
forum: General Help
---

### Post by JayWalker256 on 2013-05-16
I've got a private share set up on my home server (running Ubuntu Server 12.04.2 64-bit), such that I can mount it with a username/password. I've got it auto-mounting in /etc/fstab with the following line:

```
//192.168.1.120/jaywalker_pshare /media/server cifs username=jaywalker,password=xxx,domain=WORKGROUP 0 0
```

This worked immediately after I set it up. Though if I reboot my server while my desktop is up, I'm unable to re-mount it later. I get this fun error:

```
mount error(13): Permission deniedRefer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Which of course tells me nothing. The only solution I've found is to delete user jaywalker from smbpasswd, and re add. THEN I can re-mount the share, but that's a horrid fix. 
I'm hoping someone can shed some light on this?

The shares config is like so:

```

[jaywalker_pshare]
    comment = Jays Private Share
    path = /media/Storage/jaywalker_pshare
    valid users = jaywalker
    browsable = no
    guest ok = no
    read only = no
    directory mask 770
    create mask = 770

```

Let me know if you need more info. My desktop (the machine mounting the drive) is running Ubuntu 12.04.2 64-bit.

---

### Post by CraigPid on 2013-05-17
The only sort of practical idea I've found is to make sure you unmount the share before rebooting that machine.
   Craig

---

### Post by JayWalker256 on 2013-05-17
That isn't really a viable solution for me. Are there file sharing systems other than samba that might be better suited for my setup? I would really like to have this working so I can do automated networked backups.

---

