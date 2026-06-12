---
title: "ssh"
date: 2015-11-08
forum: General Help
---

### Post by anca-emanuel on 2015-11-08
I installed Ubuntu server 14.04 on virtualbox.
sudo apt-get install openssh-server
(edited config to accept username/password)
Then, from my PC, ssh myusername@myip
works.

How do I make it work with an key ?
And from Android ?

---

### Post by ajthemacboy on 2015-11-08
If you mean use an SSH key, this is the guide I always use: [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

---

### Post by Lars Noodén on 2015-11-08
> **ajthemacboy said:**
> If you mean use an SSH key, this is the guide I always use: [https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

The guide covers root login, at least with the mention of *PermitRootLogin*.  For Ubuntu the regular users are relevant.  For them, *PasswordAuthentication* needs to be set to "no" but only after you can verify that you can log in with your keys.

---

### Post by anca-emanuel on 2015-11-08
Some time ago I setup an key [https://launchpad.net/~anca-emanuel](https://launchpad.net/~anca-emanuel)
I do not have that PC now.
If I generate an new key, how is the best to manage it ? Save to an stick ?

---

### Post by ajgreeny on 2015-11-08
This is the best reference to start your understanding ssh and how to login
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
and for the public and private keys for login see
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by Lars Noodén on 2015-11-09
> **anca-emanuel said:**
> If I generate an new key, how is the best to manage it ? Save to an stick ?

It is best to use a strong passphrase.  For storage it is usually considered sufficient to store the private key in ~/.ssh/ on the client.

---

