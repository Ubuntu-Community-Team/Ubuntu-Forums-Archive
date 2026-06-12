---
title: "nfsd not really working"
date: 2007-01-23
forum: General Help
---

### Post by Iarwain ben-adar on 2007-01-23
Hi there,

Does anyone know why i can't mount my NFS anymore?

This is my /var/log/messages
```
Jan 23 20:15:39 Withywindle kernel: NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Jan 23 20:15:39 Withywindle kernel: NFSD: starting 90-second grace period
Jan 23 20:16:14 Withywindle kernel: portmap: server localhost not responding, timed out
Jan 23 20:16:14 Withywindle kernel: RPC: failed to contact portmap (errno -5).
Jan 23 20:16:49 Withywindle kernel: portmap: server localhost not responding, timed out
Jan 23 20:16:49 Withywindle kernel: RPC: failed to contact portmap (errno -5).
Jan 23 20:17:25 Withywindle kernel: portmap: server localhost not responding, timed out
Jan 23 20:17:25 Withywindle kernel: RPC: failed to contact portmap (errno -5).

```

This happens on the server when i try to
```
sudo /etc/init.d/nfs-kernel-server start
```

Where it hangs quite some time on 
```
Starting NFS kernel daemon: nfsd
```

What could be wrong?


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-24
*kicks it back to the top*


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-25
bump


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-26
Come on people,
someone has to know something?


Iarwain

---

### Post by Iarwain ben-adar on 2007-01-29
No one?


Iarwain

---

### Post by davedean on 2007-02-11
Hi, found your post while looking for my answer - in the end I figured my problem was some kind of client-side service not being installed by default (just upped to feisty almost by accident).

The answer for me was ..

sudo apt-get install nfs-client

Hope that helps :)

---

### Post by phantomnomad on 2007-02-21
I was receiving the same errors as above with Feisty 7.04 after upgrading by accident.

Experiencing difficulties booting whenever my network cable was plugged in, my system would time out and take a long time to boot (yes it did boot eventually).  And when it did, had to configure DNS settings manually in NetworkManager before I could access the Internet.

Anyway I,

1.  sudo apt-get --reinstall install nfs-client   (which installed nfs-common again)
2.  configured static IP settings (including DNS name servers) in /etc/network/interfaces for eth0

Now my machine boots perfectly.

Hope this helps.

---

### Post by Olav on 2007-02-21
You probably should also install portmap.

---

### Post by phantomnomad on 2007-02-21
I retract the 'perfectly' statement.. :(

I am still receiving:

...
[   74.328685] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   74.517367] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   74.539788] NFSD: starting 90-second grace period
...

in my dmesg output.. similar to above? 

Am I correct in assuming this isn't normal? I assume because of the '90-second grace period'.

---

