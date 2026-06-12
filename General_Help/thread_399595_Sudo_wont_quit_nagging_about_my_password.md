---
title: "Sudo wont quit nagging about my password"
date: 2007-04-02
forum: General Help
---

### Post by azzid on 2007-04-02
I have manipulated my .bashrc and my .bash_logout to mount and unmount a few smbshares whenever I login/logout. But since it's quite annoying to give my password twice when logging in and then once more when logging out I thought I could just edit sudoers and make myself able to run mount and unmount without supplying a password, but I cant get it to work.

This is what my /etc/sudoers look like:

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
azzid   ALL=NOPASSWD: /bin/mount *
azzid   ALL=NOPASSWD: /bin/umount *
beez    ALL=NOPASSWD: /bin/mount *
beez    ALL=NOPASSWD: /bin/umount *

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

the users azzid and beez are both in the admin group but should only be releivied from supplying their passwords when running mount or unmount.

Can someone identify my error? Getting nutts here, as far as I know the above should work. =)

---

### Post by azzid on 2007-04-02
Aha! Reading somewhat more carefully on this [wiki]("https://wiki.ubuntu.com/Sudoers") I realized the problem.

The last line in sudoers has the highest priority, so my changes had no effect since the group privilege was applied after the userprivilege. My sudoers now look like this and is working like a charm:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification
User_Alias SMBERS = azzid, beez

# Cmnd alias specification
Cmnd_Alias SMB_CMDS = /bin/mount, /bin/umount

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# User privilege specification, overriding group privileges
SMBERS  ALL=(ALL) NOPASSWD: SMB_CMDS

```

---

