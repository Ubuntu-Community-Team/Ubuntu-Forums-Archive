---
title: "SSH remote command"
date: 2013-04-29
forum: General Help
---

### Post by jonnybignote on 2013-04-29
Hello all

This is for a media center application, but I'm posting it here as I think that part is irrelevant, as is the command itself - this is more to do with the usage of SSH remotely

I'm sending a remote ssh command inside a shell script to a 11.04 server to keep it from going into standby [lock]

If I send the command remotely through terminal or even run the script through terminal, things work.

If I send it via my remote control, the command never gets sent.  The Auth.log file shows that 'failed password'.

I'm guessing a permissions thing somewhere though I'm lost as to how to find.

Any help greatly apprectiated.

---

### Post by Habitual on 2013-04-30
[key-based ssh]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and scripts are the way to go. Then such tidbits as 
```
ssh user@domain.com uptime
``` become trivial.

---

