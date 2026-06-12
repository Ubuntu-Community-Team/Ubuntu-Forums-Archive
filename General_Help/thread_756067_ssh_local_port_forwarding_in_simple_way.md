---
title: "ssh local port forwarding in simple way"
date: 2008-04-15
forum: General Help
---

### Post by qns8dn3 on 2008-04-15
To use a server with ssh local port forwarding, we should do two things, for example if we are going to connect to a Windows remote desktop over ssh, first we pen a terminal and enter :
```
ssh -L 3389:localhost:3389 username@server_address
```
Then we open another terminal and enter :
```
rdesktop -u username localhost
```

Is there a way to combine these two steps in one? 

Vnc over ssh can be done with one command :
```
vncviewer -via server server:1
```

But not every program has -via option.

---

