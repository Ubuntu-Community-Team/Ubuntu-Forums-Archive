---
title: "Getting openSSH to work"
date: 2016-02-17
forum: General Help
---

### Post by Macamba on 2016-02-17
On my new computer (Hermod, with Ubuntu 15.10) I installed openSSH server. I generated RSA Keys. I transferred the public key to my old computer (LOKI, with Ubuntu 14.04.3). Next I tried:
```
macamba@LOKI:~/.ssh$ ssh-copy-id macamba@hermod

/usr/bin/ssh-copy-id: ERROR: failed to open ID file '/home/macamba/.ssh/id_rsa': No such file

macamba@LOKI:~/.ssh$ ls -la /home/macamba/.ssh/
total 24K
drwx------  2 macamba macamba 4,0K feb 17 11:54 ./
drwxr-xr-x 81 macamba macamba  12K feb 17 11:03 ../
-rw-r--r--  1 macamba macamba  396 feb 17 11:34 id_rsa.pub

```

I succeeded with catting **[FONT=Courier New]it_rsa.pub[/FONT]** to **[FONT=Courier New]authorized_keys[/FONT]**, but when I tried to connect to hermod I got:```

macamba@LOKI:~/.ssh$ cat id_rsa.pub >> authorized_keys
macamba@LOKI:~/.ssh$ ssh macamba@hermod
ssh: Could not resolve hostname hermod: Name or service not known
```

Two problems:
[LIST]
[*]Why could I not ssh-copy-id?
[*]Why can I not connect to the new (hermod) computer?
[/LIST]

Edit:
Oh, I installed the openSSH client on the old computer (eg. LOKI).

---

### Post by steeldriver on 2016-02-17
You seem to be doing it bass-ackwards

The private key (id_rsa, by default) stays on the client computer, and the public key should be added the the authorized_keys file on the server

Usually the keypair would be generated on the client, then the public key copied to the server using ssh-copy-id, using an existing authorization mechanism (i.e. password) on the server

To get unqualified hostnames to work on a LAN, you would need to add them to your /etc/hosts file or (just for SSH) create a ~/.ssh/config file with the name-ip mapping e.g.

```

Host hermod
  Hostname        192.168.1.65
  User            macabma

```

Alternatively, you should be able to use the avahi (zeroconf) default .local domain

```

ssh macamba@hermod.local

```

---

### Post by Macamba on 2016-02-18
> **steeldriver said:**
> You seem to be doing it bass-ackwards
[/CODE]

You are right. The client should connect to the server, and therefore the public key of the client should be moved to the server (Face Palm). 

Thanks.

---

