---
title: "I have problem ssh !!!"
date: 2013-06-30
forum: General Help
---

### Post by Doud on 2013-06-30
I finished install openssh-client and openssh -server in ubuntu 10.04
and when try to writ in terminal ssh pc1 or ssh pc2
I faced this message:
ppr1@pc1:~$ ssh pc2
ppr1@pc2's password: 
Permission denied, please try again.
ppr1@pc2's password: 
Permission denied, please try again.
ppr1@pc2's password: 
Permission denied (publickey,password).
ppr1@pc1:~$ 

what can I do to solve this problem??

---

### Post by Nr90 on 2013-06-30
You might have to specify a user. You're currently trying to log in with your current user's credentials, however they might not exist on the other pc.

To do this use
```

ssh username@pc2

```

---

### Post by Doud on 2013-06-30
also
ppr1@pc1:~$ ssh ppr1@pc2
ppr1@pc2's password: 
Permission denied, please try again.
ppr1@pc2's password: 
Permission denied, please try again.
ppr1@pc2's password: 
Permission denied (publickey,password).

---

### Post by Lars Noodén on 2013-06-30
Are you sure that you have the right username, that it actually exists on the second computer and you have the correct password?  Try double checking by going to the second machine and logging in at the console with that user.

---

### Post by Nr90 on 2013-06-30
+1
To expand, you're suppost to log in with credentials that are valid on the machine you are ssh'ing TO (not credentials for the pc you are ssh'ing FROM).
Example with two PCs:
PC1:
ip: 192.168.1.2
username: user1

PC2:
ip: 192.168.1.3
username: user2

When ssh'ing from PC1 to PC2 I would use:
```

ssh user2@192.168.1.3

```

---

### Post by Doud on 2013-06-30
same MSG:
ppr1@pc1:~$ ssh ppr2@192.168.42.136
ppr2@192.168.42.136's password: 
Permission denied, please try again.
ppr2@192.168.42.136's password: 
Permission denied, please try again.
ppr2@192.168.42.136's password: 
Permission denied (publickey,password).
ppr1@pc1:~$

---

### Post by Doud on 2013-06-30
Yes Sure ...

---

### Post by Doud on 2013-06-30
> **Lars Noodén said:**
> Are you sure that you have the right username, that it actually exists on the second computer and you have the correct password?  Try double checking by going to the second machine and logging in at the console with that user.

Yes sure.

---

### Post by steeldriver on 2013-06-30
You can turn on diagnostics using the -v switch - that will let you see the connection negotiations between the two computers

```
ssh -v user@host
```

You could also use netstat on the target computer to make sure the SSH server daemon is running and listening on the expected port

```
sudo netstat -nlpt | grep sshd
```

You could also install and use nmap to probe the port from the other computer

---

### Post by Doud on 2013-06-30
ppr1@pc1:~$ ssh -v ppr2@192.168.42.136
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.42.136 [192.168.42.136] port 22.
debug1: Connection established.
debug1: identity file /home/ppr1/.ssh/identity type -1
debug1: identity file /home/ppr1/.ssh/id_rsa type -1
debug1: identity file /home/ppr1/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.42.136' is known and matches the RSA host key.
debug1: Found key in /home/ppr1/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ppr1/.ssh/identity
debug1: Trying private key: /home/ppr1/.ssh/id_rsa
debug1: Trying private key: /home/ppr1/.ssh/id_dsa
debug1: Next authentication method: password
ppr2@192.168.42.136's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
ppr2@192.168.42.136's password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
ppr2@192.168.42.136's password: 
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).
ppr1@pc1:~$

---

### Post by Doud on 2013-06-30
I am working on VMware.... and one user in each pc

---

### Post by Doud on 2013-06-30
thanks all .. I still waiting your suggestions

---

### Post by Iowan on 2013-06-30
Please be patient! It's generally polite to wait 24 hours before bumping a thread.

---

### Post by achelis on 2013-06-30
I really does look like you're typing the wrong password... Before you posted the log I was going to suggest that password login was disabled, but it looks like it is enabled on the server.

One thing you could try is to create a new user on 192.168.42.136 and then see if you can login as that user.

For example
```

sudo useradd test
sudo passwd test

```

Then login with
```

ssh test@192.168.42.136

```

Alternatively, could it be that you've mixed up the IPs?

Apart from that, I'm not sure...

---

### Post by Doud on 2013-07-01
I will install Ubuntu 11.04 now and try ....Thanks all

---

### Post by CaptainMark on 2013-07-01
Dont install 11.04, it is no longer supported so could be unsafe/unstable/insecure to use. As much as you believe you are doing it right I think your mis-understanding how to use ssh, here is a good guide for beginners [http://www.ubuntulinuxhelp.com/how-to-ssh-on-ubuntu-a-simple-guide/](http://www.ubuntulinuxhelp.com/how-to-ssh-on-ubuntu-a-simple-guide/)

---

