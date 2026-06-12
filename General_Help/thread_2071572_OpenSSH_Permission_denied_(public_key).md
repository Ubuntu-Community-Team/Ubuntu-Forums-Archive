---
title: "OpenSSH Permission denied (public key)"
date: 2012-10-15
forum: General Help
---

### Post by kwinsw on 2012-10-15
Hi,

I wonder if anyone can help. I'd really appreciate some advice. 

I've configured an Ubuntu Server 12.04 box to be an SSH server, using public-key authentication.

The key works fine when I'm remotely accessing the server from a Windows 7 PC, using PuTTY. But I just can't get my main Ubuntu Desktop 12.04 client to connect to it. 

I've done  *ssh-copy-id <username>@<host>* and this appears to have worked fine. A previously empty authorized_keys file on the client is populated. But whenever I try and connect from the terminal I get:

*Permission denied (publickey).*

On the client, I've tried running the commands:

*chmod go-w ~/*
*chmod 700 ~/.ssh*
*chmod 600 ~/.ssh/authorized_keys*

but to no avail.

Any hints as to what I'm doing wrong would be really appreciated: I'm tearing my hair out over this, and I didn't have much left to start with.

Looking at the output from ssh -vvv, it doesn't appear that the ssh client is even checking ~/.ssh/authorized_keys. 

The output from ssh -vvv is:

```
user_one@PC_ONE:~/.ssh$ ssh -vvv user_two@server
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [192.168.1.2] port 22.
debug1: Connection established.
debug1: identity file /home/user_one/.ssh/id_rsa type -1
debug1: identity file /home/user_one/.ssh/id_rsa-cert type -1
debug1: identity file /home/user_one/.ssh/id_dsa type -1
debug1: identity file /home/user_one/.ssh/id_dsa-cert type -1
debug1: identity file /home/user_one/.ssh/id_ecdsa type -1
debug1: identity file /home/user_one/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "server" from file "/home/user_one/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/user_one/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 90:f4:bb:1f:ea:be:a1:0c:eb:14:c6:11:e0:4c:62:c4
debug3: load_hostkeys: loading entries for host "server" from file "/home/user_one/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/user_one/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "192.168.1.2" from file "/home/user_one/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/user_one/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'server' is known and matches the ECDSA host key.
debug1: Found key in /home/user_one/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user_one/.ssh/id_rsa ((nil))
debug2: key: /home/user_one/.ssh/id_dsa ((nil))
debug2: key: /home/user_one/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user_one/.ssh/id_rsa
debug3: no such identity: /home/user_one/.ssh/id_rsa
debug1: Trying private key: /home/user_one/.ssh/id_dsa
debug3: no such identity: /home/user_one/.ssh/id_dsa
debug1: Trying private key: /home/user_one/.ssh/id_ecdsa
debug3: no such identity: /home/user_one/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```

Many thanks

kwinsw

---

### Post by lazarojhr16 on 2012-10-15
i go in the terminal and type:
ssh ipaddress    example  ssh 192.16X.X.X
it then asks for password, should be the password of your account.
try that and let me know.

---

### Post by drmrgd on 2012-10-15
To be sure, on the client, you've created a key with something like:

```
ssh-keygen -t rsa
```


Then copied the .pub key into the server's authorized_hosts file and retained the .private key in the client's ~/.ssh file?  It might be helpful to see your sshd_config file to be sure that there's nothing misconfigured if you've done the above and it's not working.  I'm not a professional by any stretch.  But to me the error seems to suggest that there's no match between the public key on the server and the private key on the client.

Also, since I posted this a little earlier and still have it open, here's a link with a good tutorial on setting this up that I've followed recently to help me set up and OpenSSH server:

[http://wiki.centos.org/HowTos/Network/SecuringSSH](http://wiki.centos.org/HowTos/Network/SecuringSSH)

---

### Post by kwinsw on 2012-10-16
Hi, lazarojhr16, drmrgd,

The server's set up not to allow password authenticate. Sorry, I should have made that clear. That's why I want to use a public-private key combination.

drmrgd: thanks, that link fixed the problem. But it did leave me a bit confused. I thought that point was that you created a public and private key on the server, then copied the public key to your client. 

I now log on to the server from Windows clients using the server's key that I've exported to them. But from my Ubuntu desktop, I login using the client's key, that I've exported to the server.

I need to go back and read up on this.

Still, at least I'll have somewhere to put O'Reilly's "The Secure Shell: The Definitive Guide", now that I can get the bulky old VGA monitor off my desk. ;0)

Thanks

kwinsw

---

### Post by drmrgd on 2012-10-16
We'll have to wait for one of the real networking people to chime in, but I don't understand how the Window's side is working.  It's actually backwards as you describe it. 

As I understand it, you need to export the public key to the server for the server to authenticate based on the private key held on the client.  I think I made the same mistake as you the first time I tried to set up OpenSSH as I was thinking like you.  It seems this way works and seems to be the way I ultimately found it documented.  I'm not sure why the inverse is not the way it's done, though.-

---

### Post by kwinsw on 2012-10-16
No, I'm a bit flummoxed too. I've ordered the O'Reilly book I mentioned and I'm going to read about the internet a bit. If I work it out I'll post here.

Thanks again.

---

### Post by Wayne_V on 2012-10-16
You should check what the server is doing:

- ssh to the server from your windows machine (the one that worked)
- sudo /etc/init.d/ssh stop
- sudo /usr/sbin/sshd -ddd

Now, try to ssh in from the Ubuntu machine and see why you are rejected.

When you have the logs, go back to the server and ^C to kill the debug sshd and then restart it normally (sudo /etc/init.d/sshd start)

---

### Post by Slim Odds on 2012-10-16
> **drmrgd said:**
> <cut>
As I understand it, you need to export the public key to the server for the server to authenticate based on the private key held on the client.  I think I made the same mistake as you the first time I tried to set up OpenSSH as I was thinking like you.  It seems this way works and seems to be the way I ultimately found it documented.  I'm not sure why the inverse is not the way it's done, though.-
Yes, the client has the private key. 

This makes sense since the server is the "public" side of the interface. 

Each clients key is a secret. Therefore, it must reside on the client side.

---

