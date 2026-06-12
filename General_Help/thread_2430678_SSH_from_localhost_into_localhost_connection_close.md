---
title: "SSH from localhost into localhost: connection closed"
date: 2019-11-05
forum: General Help
---

### Post by saymyname2 on 2019-11-05
I am stuck.

I try to SSH into to different accounts on the same headless computer 

I set up the SSH rsa key on all three accounts

I started the SSHD server with port 2222 

I  logged into  the VNC-Server Session of all all three accounts, copied the id_rsa.pub into the authorized.keys,  of each others account

I changed the permission on id_rsa.pub to 0600 after this 

When I try to connect to 

```
ssh -i ~/.ssh/id_rsa.pub left.screen@locahlhost -p 2222 
```

I just get a 

```
connection closed by 127.0.0.1 port 2222
```

Are there more permission necessary in the /etc/hosts.deny or .allow?

the goal is:

```
ssh -i ~/.ssh/id_rsa.pub -XC left.screen@locahlhost -p 2222 x2x -east -to :0:0 
```

---

### Post by Skaperen on 2019-11-06
be sure each account makes its own unique key pair.  each account will then have a unique id file different from every other account.  collect all the *public* keys giving each a name that identifies that user name and host name.  place all of these files in a folder of their own in a shared file server or local web server or some place that every account can read them all (just read, no write).  on each account, concatenate all the public keys together and name it "[COLOR=#0000cd][FONT=courier new]**authorized_keys**[/FONT][/COLOR]" (be sure it is readable and not writeable by other users).  put that file in the "[COLOR=#0000cd][FONT=courier new]**~/.ssh**[/FONT][/COLOR]" folder of each account.  this should now authorize these accounts to login to each other.

---

### Post by saymyname2 on 2019-11-06
That is what I did

 > I  logged into  the VNC-Server Session of all all three accounts, copied  the id_rsa.pub into the authorized.keys,  of each others account

---

### Post by The Cog on 2019-11-06
* .ssh and everything in it must be owned by the appropriate user.
* ./ssh must be accessible only by that user (drwx------).
* .ssh/authorized_keys must be accessible only by that user (-rw-------).

ssh -v will output a lot of progress info which may help debug. Also, /var/log/auth.log will contain some log messages giving the server's point of view.

---

### Post by saymyname2 on 2019-11-06
mus be owned, that is what I wrote:

> I changed the permission on id_rsa.pub to 0600 after this

had already been asked to do so. the permission are  right. Debug tells me:

```
left.screen@localhost:~/Desktop$ ssh -v middle.screen@localhost -p 2222
OpenSSH_7.6p1 Ubuntu-4, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 2222.
debug1: Connection established.
debug1: identity file /home/left.screen/.ssh/id_rsa type 0
debug1: key_load_public: No such file or directory
[...]
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4
debug1: match: OpenSSH_7.6p1 Ubuntu-4 pat OpenSSH* compat 0x04000000
debug1: Authenticating to localhost:2222 as 'left.screen2'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: [....KEY...]
debug1: **Host '[localhost]:2222' is known and matches the ECDSA host key**.
debug1: **Found key in /home/left.screen/.ssh/known_hosts:1**
debug1: **rekey after 134217728 blocks**
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug1: **SSH2_MSG_SERVICE_ACCEPT received**
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: RSA [..KEY...] /home/left.screen/.ssh/id_rsa
debug1:** Server accepts key: pkalg rsa-sha2-512 blen 279**
** Enter passphrase for key '/home/left.screen/.ssh/id_rsa': **
Connection closed by 127.0.0.1 port 2222
left.screen@localhost:~/Desktop$ 


```

---

### Post by Holger_Gehrke on 2019-11-06
As far as I can see you made two different mistakes ...
In post #1 you used id_rsa.pub as your identity-file. That's the **public** key, unless you renamed the file. You should have used the **secret** key id_rsa.
In post #5 you didn't give an identity-file, but did give a user name that's not the one you're logged in as. Without an identity file, ssh defaults to ~/.ssh/id_rsa as the identity file. That's probably the secret key for left-screen@localhost, but you're trying to log in as middle.screen@localhost ...

Holger

---

### Post by saymyname2 on 2019-11-06
Ähm.

Did you read the code output?

The public key needs to be copied into the authorized keys files. that is what I did.  The key file permissions must be set to read only by owner = 0600 I did that.

I highlighted the significant parts of the -vvv output.

---

### Post by TheFu on 2019-11-06
No need to make things hard.  To setup keys, 2 commands are needed.```

$ **ssh-keygen** -t ed25519
$ **ssh-copy-id** -i ~/.ssh/id_ed25519.pub userid@remote
```

This handles using the stronger ed25519 keys, not RSA.
The 2nd command puts the public key on the remote system correctly.  It doesn't screw up permissions.

[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has more details and ideas.

---

### Post by saymyname2 on 2019-11-06
The keys are not the problem.
See above output of SSH -vvv
It clearly says key accepted.
The permissions are fixed the first thing after SSH output warned to permissive right from 0640 to 0600
And are correctly set

I think I have to work on /etc/hosts.deny and /etc/hosts.allw

---

### Post by Skaperen on 2019-11-06
as long as you continue to do the same thing and remain convinced that everything you are doing is correct, there will be no resolution, and everyone will become tired of trying to help.  i see these things going on:

1.  you really are using a .pub key for your identity (-i option).  that's not the right way no matter what you think the messages mean.  but it looks like ssh figured out your mistake and corrected for it.

2.  in all those event status messages you got (near the end) "Enter passphrase for key '/home/left.screen/.ssh/id_rsa':".  that tells us that the real identity key is encrypted.  when you created the key pair, the identity key (the one without ".pub" at the end of the name).  ssh-keygen always uses a pass phrase to encrypt the key except in certain cases.  but somehow yours got encrypted.  that's easy to happen.

i think it would be a good idea to start all over from a blank slate.  let us tell you what steps take.  then when you get error messages, let us be the ones to interpret them.  once we get you working and you make a backup, then you can customize it as you wish.

---

### Post by saymyname2 on 2019-11-07
I am not using the .pub for identification, but SSH checks if the .pub key is in your ~/.ssh directory and demands a 0600 on it.  It is using the the right key.  I get identified towards the ssh-server, the -vvvv output says:      ```
 debug1: Offering public key: RSA [..KEY...] /home/left.screen/.ssh/id_rsa debug1: Server accepts key: pkalg rsa-sha2-512 blen 279  Enter passphrase for key '/home/left.screen/.ssh/id_rsa': 
```         I see a an issue either with either   ```
    /etc/ssh/ssh_config   
```      OR with     ```
 /etc/security/ ???.conf    
```      ```
  ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote 
```   does not work.  I tried that before.  Actually one more issue. This is Ubuntu running on Termux running on Android and /proc is apparantly not accessible. And SSH appears to need access to proc.

---

### Post by saymyname2 on 2019-11-09
In etc/passwd  sshd is set to nologin. Correct?

---

