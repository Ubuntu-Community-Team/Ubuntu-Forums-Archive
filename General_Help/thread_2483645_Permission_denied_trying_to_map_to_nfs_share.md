---
title: "Permission denied trying to map to nfs share"
date: 2023-02-05
forum: General Help
---

### Post by easygoing1 on 2023-02-05
Hello,

I have a clean install of Ubuntu 22.04 server in an ESXi VM. After installation, I merely did

```
sudo apt update / sudo apt upgrade
```

then


```
sudo apt install nfs-kernel-server -y
sudo systemctl start nfs-server
sudo systemctl enable nfs-server

```

Next, I created a folder:```
 /media/test
```

Then I added this to /etc/exports: ```
/media/test *(rw,async,no_subtree_check,no_root_squash)
```

Then I ran ```
sudo exportfs -avr
```

On the client, I made folder in my home path: ```
/Users/michael/test
``` then I ran

```
mount -t nfs 10.10.11.45:test /Users/michael/test
```

and I get permission denied

if I try

```
mount -t nfs 10.10.11.45:/media/test /Users/michael/test
```

I get Operation not permitted

From the server when I run who it gives me this:

```
michael  pts/0        2023-02-05 18:48 (10.10.10.90)
```

Which is the IP of my laptop and my username (same username and password on both machines)

I've tried chowning /media/test to my username and restarting nds service and issuing exportfs again and that didn't help...

I even rebooted the server just to be thorough ... no joy.

Any ideas?

---

### Post by DuckHook on 2023-02-05
Welcome to the forums, easygoing1,

Please use standard fonts and styles when posting. Odd fonts/styles are difficult to read on small screens. Also, use *CODE* tags for output to preserve content and format.

As to your question:

To my knowledge, you can't mount standard NFS shares as user. Must be admin. Try it with sudo. You can then configure server and client using uids to fine tune user access. Standard practice is to put the mount under root as well, traditionally /mnt, then control access with uid/owner/privilege settings instead of mounting into /home which creates obscure issues (mainly to do with /home having non-admin ownership for a mount that is by design an admin function). If you for some reason must mount the share as an unprivileged one, then you can try using FUSE, but I have never done that and cannot help you through the process, although here is a link that might: [https://github.com/sahlberg/fuse-nfs/blob/master/README](https://github.com/sahlberg/fuse-nfs/blob/master/README)

Only peripherally related to your question, but I also find it more convenient when working with network shares to do so using autofs instead of monkeying with my fstab. Autofs will automount those NFS shares only when needed and will drop/unmount them after a period of inactivity. This greatly reduces the load on my network and, even better, makes my system more robust because it won't freeze up should my network experience a hiccup that nukes the NFS share. fstab works at a very primitive level, so when an NFS share suddenly goes missing, the kernel panics because it thinks it is missing its liver. Autofs is smarter and fails more gracefully.

---

