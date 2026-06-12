---
title: "setting up ssh keys"
date: 2021-08-22
forum: General Help
---

### Post by Old Jimma on 2021-08-22
Hello forum:

I am having trouble setting up ssh keys.

I've followed the Ubuntu documentation at > [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) and used a passphrase.

On the client I use:

> 
mkdir ~/.ssh
chmod 700 ~/.ssh
ssh-keygen -t rsa


In transferring the client key to the host I used:

> 
ssh-copy-id <username>@<host>


where <usernam> is the username on the server, and <host? is the ip address of the host.

I got the message:

> 
usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 192.168.1.136 port 22: Connection refused




What do I do to fix this? 

Thanks,
Old

---

### Post by TheFu on 2021-08-22
The "ssh" package needs to be installed on both the client and the server.

---

