---
title: "[SOLVED] SSH Configuration?"
date: 2008-03-23
forum: General Help
---

### Post by parrimin on 2008-03-23
Hey, i just installed ssh on my ubuntu, redirected port 22 of my router to the Ubuntu PC, and opene dyndns.org account.

Now, im trying to connect from windows with putty. If i type the local ip, it runs ok
If i type the external ip, or the dyndns, it connects ok to the ssh server, i put the username, and it says Access denied.

So, I think i missed something to configure in my server, because now in the prompot it says:
[email]myusername@mydns.dyndns.org[/email]

I think my machine is refusing because the mydns.dyndns.org... or maybe i dont have any idea how this is to be configured.. or.... help plz :lolflag:

---

### Post by Joeb454 on 2008-03-23
say your dyndns thing is parrimin.thruhere.net

```
ssh username@parrimin.thruhere.net
``` should work

You installed ***openssh-server*** on your ubuntu machine didn't you?

---

### Post by parrimin on 2008-03-23
> **Joeb454 said:**
> say your dyndns thing is parrimin.thruhere.net

```
ssh username@parrimin.thruhere.net
``` should work

You installed ***openssh-server*** on your ubuntu machine didn't you?

Yes, i installed ssh server, or so i think. I typed sudo apt-get install ssh...

I can connect to ssh from putty if i type

192.168.1.3
Then it prompts to enter the username, and then the password. All run ok.

But if i type
mydomain.dyndns.org
it prompts to enter the username, when entered, and then the password, it says access denied.

---

### Post by jeffus_il on 2008-03-23
If you don't solve the problem, look in /etc/ssh/sshd_config at the authentication section, you may find something there.

---

### Post by parrimin on 2008-03-23
Now im searching info on how to configure /etc/hosts. Dont you think i have to edit it to my server to know that localhost and mydomain.dyndsn.org are the same?

But i dont have any idea on how this functionality runs...

---

### Post by Joeb454 on 2008-03-23
No you shouldn't have to edit anything (except forwarding port 22 on your router to the box you want to ssh to :))

try running ```
sudo aptitude install openssh-server
``` and then try using the domain name instead :)

---

### Post by parrimin on 2008-03-23
Sorry, i think you guys are not understanding my problem, of course because of my poor english...

I have ssh server installed and running. I can connect to it within my home lan typing the internal ip.

I have installed in that ubunt machine a apache server, and ssh server.

I have routed port 80 and port 22 to that machine.

I have created an account in dyndns.org to redirect yo my dynamic ip.

If I ping to my dyndns.org, it resolves ok.

If i go in a browser to mydomain.dyndns.org, it  opens my welcome page.

If i try to connect to mydomain.dyndns.org, it connects. It connects, but im not able to log on. I put my user and password, and it says is wrong.

I cant understand how /etc/hosts can help, it was only a suggestion

---

### Post by Ramses de Norre on 2008-03-23
The same procedure does work here (also with a dyndns account), are your /etc/hosts.{deny,allow} configured correctly? Can you connect over ssh from the server to itself using the dyndns domain? Try running with ssh -v to get debug messages.

---

### Post by kevdog on 2008-03-23
ssh -vvv user@host

That is 3 v's to show debugging info.  You shouldn't need to mess with the hosts file.  You did open up port 22 on the server's firewall??? (On ubuntu using firestarter, guarddog, or by modifying the iptables manually)?

---

### Post by parrimin on 2008-03-23
> **Ramses de Norre said:**
> The same procedure does work here (also with a dyndns account), are your /etc/hosts.{deny,allow} configured correctly? Can you connect over ssh from the server to itself using the dyndns domain? Try running with ssh -v to get debug messages.

/etc/hosts deny allow... i have not configured anything on that file, i dont know how to touch it.

I can't try to connect to itself, because the machine has some problem, after installing, and updating from repositories, it started to not showing anything, but machine is runnign, because i can connect via putty (ssh).

So i cant test ssh -v

---

### Post by Ramses de Norre on 2008-03-23
I don't know about ubuntu but on most distros hosts.deny contains ALL:ALL and hosts.allow nothing, in that case you need to explicitly add sshd to hosts.allow.
I'm afraid you'll need to get the server fixed though, It's quite hard to find the problem without debug info.

---

### Post by kevdog on 2008-03-23
Within Putty why don't you activate the logging option?

---

### Post by parrimin on 2008-03-24
> 
user@user-server:~$ ssh mydns.dyndns.org
The authenticity of host 'mydns.dyndns.org (87.221.22.34)' can't be established.
RSA key fingerprint is f8:76:e5:f9:17:6d:b9:ea:52:96:33:64:f8:1e:7e:1d.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'mydns.dyndns.org,87.221.22.34' (RSA) to the list of known hosts.
[email]user@mydns.dyndns.org[/email]'s password: 
Permission denied, please try again.
[email]user@mydns.dyndns.org[/email]'s password: 



This is the exact message i see. Now im connectinc from ubuntu command line to itself connecting to mydns.dyndns.org

---

### Post by parrimin on 2008-03-24
> 
user@user-server:~$ ssh -v mydns.dyndns.org
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to mydns.dyndns.org [87.221.22.34] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_3.6p1
debug1: match: OpenSSH_3.6p1 pat OpenSSH_3.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client 3des-cbc hmac-sha1 none
debug1: kex: client->server 3des-cbc hmac-sha1 none
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host 'mydns.dyndns.org' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Next authentication method: password
[email]user@mydns.dyndns.org[/email]'s password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
[email]user@mydns.dyndns.org[/email]'s password: 
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.


This is the output message in debug mode. Help...

---

### Post by kevdog on 2008-03-24
Definitely seems the password is incorrect or an authentication problem.  The server is running ubuntu?  Does the user have an account on the server (or ubuntu machine)?  Is the password correct for the user?

I dont think its going to make a difference but shouldn't this:
ssh -v mydns.dyndns.org

Really be:

ssh -v <username>@mydns.dyndns.org

---

### Post by parrimin on 2008-03-26
> **kevdog said:**
> Definitely seems the password is incorrect or an authentication problem.  The server is running ubuntu?  Does the user have an account on the server (or ubuntu machine)?  Is the password correct for the user?

I dont think its going to make a difference but shouldn't this:
ssh -v mydns.dyndns.org

Really be:

ssh -v <username>@mydns.dyndns.org

If i put ssh -v [email]user@mydns.dyndns.org[/email], it says the same, Access denied

If i put ssh 192.168.1.3 (the lan ip), i can access with the same user and password with no problem.

If i put ssh 87.221.23.253 (external ip), it says access denied when i enter username and password.

---

### Post by parrimin on 2008-03-27
I'va solved it!!!!!
I found a blog where someone have explained how to minimal security settings on ssh, for a dummy like me ;P . I only had to add the line:

 ```
AllowUsers myuser
```

in /etc/ssh/sshd_config

I can connect throught mydns.dyndns.org !!!!!

I hope this would be useful for someone else. If anyone can speak spanish, here is the tutorial:

[http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/](http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/)

---

