---
title: "bash script to launch remote app via ssh"
date: 2007-05-09
forum: General Help
---

### Post by Hakimio on 2007-05-09
I need a bash script, which would launch gkrellm on a remote pc. Here are the commands I use:
```
ssh -X USER@192.168.1.1 -p 2222
[ENTER my pass]
gkrellm &
```
Is it possible to make a bash script for this?

---

### Post by stylishpants on 2007-05-09
You are basically there already.

The command you need is:
```
ssh -X USER@192.168.1.1 -p 2222 gkrellm
```

You may want to set up a passwordless ssh login to the remote system too.  You'd need that if you want to add an '&' to the end of the command.

---

### Post by Hakimio on 2007-05-09
Thanks, but isn't there a way to make bash script enter a pass for me?

Edit: Just made a passwordless authentication with dsa public key :)

---

### Post by Railsbuntu on 2008-07-06
And what if I wanted to run more than one commande? How does the disconnection occur?

---

