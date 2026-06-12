---
title: "Permissions Appear Correct, but Fail"
date: 2020-02-17
forum: General Help
---

### Post by humanjhawkins on 2020-02-17
I'm running a dockerized Minecraft server (itzg/minecraft) in a fairly straightforward Ubuntu 18.04 server. The Minecraft directory is under /srv. If I [COLOR=#0000ff][FONT=courier new]sudo chmod 777 -R /srv[/FONT][/COLOR], everything works great. So I know my issue is permissions related. However, I am not able to get it to work correctly otherwise, unless I make a specific account (not group) the owner of the server's file store.

I've done this:
```
sudo groupadd gameadmin
sudo usermod -a -G gameadmin myUsername
sudo chown -R root:gameadmin /srv
```

If I then do [COLOR=#0000ff][FONT=courier new]sudo chmod 775 -R /srv[/FONT][/COLOR], minecraft fails to save user progress. However, if I [COLOR=#0000ff][FONT=courier new]sudo chown -R myUsername:gameadmin /srv[/FONT][/COLOR], it works. I've also confirmed that the gameadmin group has myUsername in it with [COLOR=#0000ff][FONT=courier new]getent group gameadmin[/FONT][/COLOR]. 

How can it be that with 775 permissions, the account owner and group owner do not have the same ability to write/modify files and directories?

Thanks in advance.

---

### Post by TheFu on 2020-02-17
Are permissions, users, and groups inside the container the same as outside the container?  Just asking.  Only you would know.

---

### Post by Skaperen on 2020-02-17
are you doing the chown commands inside the container or outside?

---

### Post by TheFu on 2020-02-18
> **Skaperen said:**
> are you doing the chown commands inside the container or outside?

Hopefully, there isn't any way to get "inside" a running container.  That would be bad, against container best practices, and defeat the purpose.  Containers should only have enough OS to do the 1-thing they are supposed to do.  No shell. No ssh.  Just 1 running program, hopefully, just a single network service. 

Don't leave any tools helpful to an attacker inside the container.  It should only be able to run the single program, nothing else.

At least that's what the training I've had beat into our heads.

---

