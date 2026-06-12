---
title: "ssh-agent, ssh-add and ssh in a script"
date: 2016-07-06
forum: General Help
---

### Post by EssexEagle on 2016-07-06
For work I often have to SSH into another machine, which I can do by running the following three commands in succession from the command line:
```
eval `ssh-agent`
```
```
ssh-add -l | grep -q `ssh-keygen -lf ~/.ssh/id_rsa_*MACHINE_NAME*  | awk '{print $2}'` || ssh-add ~/.ssh/id_rsa_*MACHINE_NAME*
```
```
ssh -AY *USERNAME*@*HOST*
```

However, it's a bit annoying to write these commands out every time (even though I have them saved in a text file so I can just copy and paste them).  But when I put them in a script as follows
```
#!/bin/bash
eval `ssh-agent`
ssh-add -l | grep -q `ssh-keygen -lf ~/.ssh/id_rsa_*MACHINE_NAME*  | awk '{print $2}'` || ssh-add ~/.ssh/id_rsa_*MACHINE_NAME*
ssh -AY *USERNAME*@*HOST*
```
it doesn't work.  When I run the ssh-agent command from the command line I get a message like "Agent pid *N*" and when I run the ssh-add command I have to put in my passphrase.  But when run from my script they don't seem to have any effect.  Is there a way of putting these into a script so I can just run that script, type in my passphrase and be logged in to the remote machine automatically?

---

### Post by DuckHook on 2016-07-07
*Thread moved to **General Help** as the more appropriate forum.*

---

