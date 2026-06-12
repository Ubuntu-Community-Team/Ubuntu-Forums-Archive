---
title: "Chroot directory limit user to sftp folder"
date: 2015-04-23
forum: General Help
---

### Post by rob134 on 2015-04-23
Hi,
I'm trying to limit a user to a spefic existing website domain folder. Even with the online documentation I can't seem to figure this one out.
My current setup **which works**: sshd_config file:
```
Subsystem sftp internal-sftp
```

```
Match group filetransfer2
    ChrootDirectory %h
    X11Forwarding no
    AllowTcpForwarding no
    ForceCommand internal-sftp
```

**ubuntu commands I ran:**
```
addgroup --system filetransfer
usermod -G filetransfer username
chown root:root /home/username
chmod 755 /home/username
cd /home/username
mkdir docs public_html
chown username:filetransfer *
```

And the username is restricted to /home/username folder and works perfectly. **Now what i try to do is limit username to:** /home/somefolder/public/domain.com/
When I use sudo usermod --home /home/somefolder/public/domain.com/username it changes the default directory of username when logged in with sftp. Although it refuses to login. I've also tried all the above steps while using /home/somefolder/public/domain.com/ without luck, it refuses to login sftp.
I have to give some support desk my sftp login and obviously I don't want to give them my root login details and therefor want to limit them to the domain.com folder.
What am I doing wrong?
Thanks
Rob

---

### Post by sandyd on 2015-04-23
Check /var/log/audit.log - should be some errors there.

Paste them here, and we can go from there :)

---

### Post by rob134 on 2015-04-23
> **sandyd said:**
> Check /var/log/audit.log - should be some errors there.

Paste them here, and we can go from there :)
I had to chown root:root the folders that were above that. It works now. Thanks for the tip about the log :)

---

