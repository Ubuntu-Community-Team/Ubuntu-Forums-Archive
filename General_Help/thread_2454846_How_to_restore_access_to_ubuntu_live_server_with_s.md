---
title: "How to restore access to ubuntu live server with ssh ?"
date: 2020-12-07
forum: General Help
---

### Post by petrogromovo on 2020-12-07
Hello,
I changed  ssh keys on my local ubuntu 18 and lost access to ubuntu 18 live server with ssh. 
I can enter the system with password. 
Have I to replace content of id_rsa from my local ubuntu 
into id_rsa of live server ?
Are there some other actions I have to tak e?

Next restart OS?

Thanks!

---

### Post by ActionParsnip on 2020-12-07
you can add the new public key alongside the old one. You can have lots of public keys in ~/.ssh/authorized_keys without issue
The key file is read when the SSH connection is made so no need to reboot.
Just specify the new private key in your client and away you go

---

### Post by skipbarker on 2020-12-07
SSH copy id is what you want to use to get the new key over.
> ssh-copy-id -i ~/.ssh/your-new-key.pub user@your-live-server

---

