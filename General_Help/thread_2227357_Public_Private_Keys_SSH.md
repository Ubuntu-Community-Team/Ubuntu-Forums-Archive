---
title: "Public Private Keys SSH"
date: 2014-06-01
forum: General Help
---

### Post by nathan35 on 2014-06-01
Afternoon guys

I have a clean install of server 12.04, SSH is fully working with out keys at the moment.  So far i have

```


ssh-keygen -t rsaEnter file in which to save the key (/home/****/.ssh/id_rsa):Enter passphrase (empty for no passphrase):

```

Once the authorized_keys is created i then proceed too create a new set of keys from puttygen.  So new public/private key generated I remove the text in autorized_keys and replace it with the public key from puttygen.  I save the private key on my windows computer and setup putty the way I have before.

Now this is the weird part.  If i open putty and login automatically with the key, it will say (Server refused our key) Enter password...  If i enter password and then proceed too open another instance of putty it will logging successful with the key that just failed..  Any ideas?

---

### Post by TheFu on 2014-06-01
Check the log files on both the client and the server. You can enable higher log levels as needed on the server side. They are usually very helpful.

---

