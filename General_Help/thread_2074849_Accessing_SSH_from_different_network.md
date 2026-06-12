---
title: "Accessing SSH from different network"
date: 2012-10-22
forum: General Help
---

### Post by souar on 2012-10-22
Hey 

I've got SSH up and running on Ubuntu server 12.04 just fine and can get access from it on my local network easily. However I cannot figure out how to access it from a different network? 

What do I need to change/add to make this possible? Also some clarification on using keys would be fantastic as I have no idea how to?

Thanks

---

### Post by Lars Noodén on 2012-10-22
If you're talking about the usual home setup, you'll need to set up port forwarding on your router.  One port, usually 22, on your external IP address needs to get forwarded to port 22 on the machine running OpenSSH server.  The details of port forwarding vary from model to model.

---

### Post by Lars Noodén on 2012-10-22
About keys, there is a lot of material about how to use them.  Here is the community documentation for Ubuntu:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

In short, you need a public-private key pair and the public key goes into the file ~/.ssh/authorized_keys on the server while the private key stays on the client.  

Here is a more detailed description of how to set up key-based authentication:
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Key-based_authentication.2C_basic](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Key-based_Authentication#Key-based_authentication.2C_basic)

However, there is any number of other resources explaining how to do it.

---

### Post by souar on 2012-10-22
Ahhh that's odd I had set all that but it wasn't working but now it is. Guess it just takes a moment to take effect.

It worked fine when I tried accessing the server using the external IP address on the work network but now I'm home and trying again it will connect but when I try and login either as 'root' or 'system' and type in the password it says 'access denied', why is this now happening?

---

### Post by Lars Noodén on 2012-10-22
It's generally considered a good thing to keep remote root login disabled.  It prevents a lot of types of trouble.

```

PermitRootLogin no

```

---

### Post by souar on 2012-10-22
Ahhh so the only way I can activate it is once i'm back in the office on the same network and can change the config file? 

If this isn't a particularly safe way of accessing and controlling the server do you have any suggestions of what is? I need to be able to access the files and run the server remotely. For the files is there anyway of having a more graphical interface like explorer with samba while accessing it remotely?

Thanks for this help its really appreciated!

---

### Post by efflandt on 2012-10-22
Many broadband routers or Linux itself used to masquerade a private network as a public IP, don't do loopback (LAN2LAN via public IP) maybe because it is difficult to tell if an IP coming in on a public interface belongs there or is spoofed.  So if you want to see if something is accessible from the internet it is best to test that from some computer (or *nix shell account) that is not on your LAN and has some other internet connection.

I normally configure any ssh server to use keys only and disable root login (use sudo instead).  That way crackers can try passwords forever and none will work.

I have not really tried using **sftp** (which is ssh related secure ftp) because the few times I transfer files over the internet, I know where they are or where they go to, so I just use **scp** to copy them over securely.  But that is typically just to upload files to web space related to a shell account on servers that run NetBSD.  Although, they also use Ubuntu for minecraft game servers.

---

### Post by Cheesehead on 2012-10-22
> **souar said:**
> I need to be able to access the files and run the server remotely. For the files is there anyway of having a more graphical interface like explorer with samba while accessing it remotely?

If you determine that your router forwards ssh, then you certainly can.

I use the sshfs package on my client (nothing extra is needed on the server). Mounts an ssh connection as a network drive - everything shows up in the file manager normally, file transfers 'just work', etc.

Or you can use Samba. Or several other alternatives.

Depending upon how much GUI you need, you can even install X on the server, and use 'ssh -X' to use the client's screen and mouse to control the server's X session. It's not RDP or VNC (sharing), it's running a server X session remotely via SSH.

---

### Post by Lars Noodén on 2012-10-23
> **souar said:**
> Ahhh so the only way I can activate it is once i'm back in the office on the same network and can change the config file? 


The way to do that is to log in and use sudo or su to take care of tasks that need privileges.  Also, sudo is not an all or nothing proposition.  You can add specific programs and scripts to it, too.

```

%adm ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service

```

---

### Post by Lars Noodén on 2012-10-23
> **Cheesehead said:**
> Depending upon how much GUI you need, you can even install X on the server, and use 'ssh -X' to use the client's screen and mouse to control the server's X session. It's not RDP or VNC (sharing), it's running a server X session remotely via SSH.

As far as I know to do that you don't need X installed on the server.  The X server itself is on the client and that's the one the remote ports are forwarded to.  Yes, it seems a bit backwards, but that's how the architecture is set up.  Anyway, tunneling X works for giving you graphical applications.

Another options is to use SSHFS to mount the remote file system as a local folder.  That is easy to set up.

---

