---
title: "Backintime with root and ssh"
date: 2015-10-30
forum: General Help
---

### Post by dameffy on 2015-10-30
Hello there!
I'm still fiddling around with Backintime in root mode and ssh. I created both the key pairs for user and root as explained in the manpage of BiT.
So I'm starting BiT as root, enter the IP address of the server etc, and as user I enter my user name and not root (correct...?). But now I get the error "Can't write to /root/.local/share/backintime/mnt/tmp_1_13006/backintime/...". I guess the problem is that sshfs mounts the server to the root directory where I do not have access as user that will be logged in by ssh. So where is the trick?? I do not fully understand the root mode of BiT. Concerning to this message I should log in as root on the server so that the access rights ar5e correct, but I don't think this is the intention...
I really would appreciate any help because, well, I just don't understand it :p

---

### Post by slickymaster on 2015-10-30
Hi dameffy, welcome to the forums.

I've moved your thread to the **General Help** sub-forum because the Tutorials is for Ubuntu related Tutorials and Howtos.

---

### Post by Germar on 2015-10-30
> **dameffy said:**
> 
I created both the key pairs for user and root

If you only want to run BIT as root you only need a key for your local root user and copy that public key to your remote user

> 
So I'm starting BiT as root, enter the IP address of the server etc, and as user I enter my user name and not root (correct...?).

You need to enter the username from your remote server. That could be the same as your local username but doesn't need to.

> 
But now I get the error "Can't write to /root/.local/share/backintime/mnt/tmp_1_13006/backintime/...". I guess the problem is that sshfs mounts the server to the root directory where I do not have access as user that will be logged in by ssh.

Nope. If you started BIT as root than it has access to /root. As explained above that user is on REMOTE server.

I'm not sure what causes this. I first thought your remote user has no write access on the given path. But I check this before mounting with sshfs.

Please install current stable version 1.1.8 from our PPA, start BIT from Terminal, try to configure it again and post the output if it fails again:

```
sudo add-apt-repository ppa:bit-team/stable
sudo apt-get update
sudo apt-get upgrade
pkexec backintime-qt4
```

[SIZE=1]Disclaimer: I'm member of BIT Dev-Team[/SIZE]

---

### Post by dameffy on 2015-11-01
Hello Germar!
    Thanks for your reply! Unfortunately I still get the error "Can't write to: /root/.local/share/backintime/mnt/tmp_1_6120" with version 1.1.8 :-(. If it helps: when I change to this folder write permissions are only set for root (so far so good...). If I go into this folder to /root/.local/share/backintime/mnt/tmp_1_6120/backintime/backintime this one seems to have permission set to 777. When I create a file here this one has the owner of the remote user...That's the point where I get confused...
Thanks!

---

