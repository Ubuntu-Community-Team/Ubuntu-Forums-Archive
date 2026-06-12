---
title: "[SOLVED] How can I start tpb when I start the system"
date: 2007-08-13
forum: General Help
---

### Post by holihue on 2007-08-13
How can I have tpb to start when my system booting?
I added tpb -d in /etc/rc.local, but it doesn't work.

It needs root to start so I can't add it to startup session.

I can add it to the startup session, but then I must type my password to start it(I think).



Thanks

---

### Post by holihue on 2007-09-11
I did a:
```
sudo chown myname:myname /dev/nvram
```

and then I added tpb to System>Preferences>Session.

Is this a good idea, or will it be a problem with that?

---

### Post by holihue on 2007-09-13
And I had to add:
```
chown name:name /dev/nvram
```

to /etc/rc.local

Now it works perfect.:):):):):)

---

### Post by DStensland on 2007-11-28
Here's how I got tpb working on my ThinkPad A21m (2628-F2U)

1) Use Synaptic to install the tpb package

2) Open a terminal and at the command prompt gedit /etc/group.  Find the line that has nvram in it and add your login name to the end of that line after the colon.

3) Go to System>Preferences>Session, then add a tpb entry to the startup tab

Reboot and it should be working. Note: There was no need to edit the rc.local file this way.

---

