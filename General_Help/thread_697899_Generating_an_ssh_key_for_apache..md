---
title: "Generating an ssh key for apache."
date: 2008-02-15
forum: General Help
---

### Post by mlitteken on 2008-02-15
I'm going to try to explain this, and hopefully it comes out intelligible mostly.

I want to set apache up with a ssh key on a few computers in a local network so that I can have PHP execute an SCP call to transfer a file to these computers. I've tried logging in as www-data with sudo su www-data, but www-data doesn't have the privileges (I'm sure for very good reason) to create an ssh key or do anything. So I'm a bit stuck. Is what I'm trying to do even possible? Thanks!

-Matthaus

---

### Post by PinkFloyd102489 on 2008-02-15
Open a terminal and do this:

```

ssh-keygen

```

It'll start generating the keys, which make take a little bit. Output should look like this:

```

user@host$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/user/.ssh/id_rsa.
Your public key has been saved in /home/user/.ssh/id_rsa.pub.
The key fingerprint is:
XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX user@host

```


I suggest using a password that is at least 10 characters long, with numbers, letters, and other characters like @ and &.

The key is stored in ~/.ssh/

---

### Post by mlitteken on 2008-02-15
Sorry, maybe I wasn't clear enough. I have run ssh-keygen while logged in as www-data, but www-data doesn't have sufficient privileges to create files and directories for an ssh-key.

---

### Post by PinkFloyd102489 on 2008-02-15
www-data is a system user so I dont think you'll be able to create an ssh key for it.

---

