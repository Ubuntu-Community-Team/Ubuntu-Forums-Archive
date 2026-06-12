---
title: "trouble with  ssh-copy-id"
date: 2022-06-16
forum: General Help
---

### Post by Old Jimma on 2022-06-16
Hello Forum People:

I have a server machine with IP 192.168.1.136

I've created a ssh password on my server machine using

> 
 ssh-keygen -t rsa


That seems to work well.

Then, I issue a command to share the ssh keys with a client machine:

>  ssh-copy-id auggie@192.168.1.181

and I get the message:

> 
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/pi/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 192.168.1.181 port 22: Connection refused


Looks like my client refused the keys on port 22 (ssh).

So, on that client machine I issued:

> 
sudo ufw enable
sudeo ufw allow from any port 192.168.1.136 to any port 22 


and then I rebooted the client machine, and issued the command

>  ssh-copy-id auggie@192.168.1.181 

and get the same error message:


> 
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/pi/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed

/usr/bin/ssh-copy-id: ERROR: ssh: connect to host 192.168.1.181 port 22: Connection refused


How do I get the client to accept the ssh keys?

Old Tired Jimma

---

### Post by TheFu on 2022-06-16
What does 
$ ssh -vvvvv user@ip 
show?
I suspect an issue with ssh.

BTW, these days, we shouldn't really use RSA keys.  We need 4K keys or use any of the elliptical options.


Why would you use 
ssh-copy-id auggie@192.168.1.181 
when the server is at auggie@192.168.1.136?
I'm confused.

ssh keys are created on the ssh client and the public key is pushed to the ssh server.

---

### Post by Old Jimma on 2022-06-17
Hi TheFu:

Thanks for your reply.

The sever is: pi$192.168.1.136 and the client is auggie@192.168.1.181

On the server, ssh -vvvv auggie@192.168.1.181 is

> 
$ ssh -vvvv auggie@192.168.1.181
OpenSSH_7.9p1 Raspbian-10+deb10u2+rpt1, OpenSSL 1.1.1n  15 Mar 2022
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.1.181 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.168.1.181 [192.168.1.181] port 22.
debug1: connect to address 192.168.1.181 port 22: Connection refused
ssh: connect to host **192.168.1.181 port 22: Connection refused**


I get this message although I've set the firewall on auggie@192.168.1.181 to allow incoming tcp on port 22 from 192.168.1.136

You wrote:
> 
ssh keys are created on the ssh client and the public key is pushed to the ssh server. 


This makes me thing that I'm using the words "client" and "sever" incorrectly and what I mean as "client" is a server, and what I mean as "server" is a client.

Here is the background: I'm using a pi to do backups of my other ubuntu machines. I think of the pi as the server, and each of the other ubuntu machines as clients. Do I have my terminology backwards??

In any case, the pi doing the backups must give its .ssh directory to all of other ubuntu machines using 

> 
ssh-copy-id auggie@192.168.1.181


for example. And all of the other ubuntu machines must have the same .ssh directory as the .ssh directory on the pi that does the backup, right?

This is a part of a project you recommended 9 months ago. I have to go thru the same process of getting the machines set up because some wires on the pi machine got loose, and during a backup the pi backup wrote over the OS on the SSD card because a hard disks was no longer mounted because of the loose usb connection that didn't allow a hard drive to be mounted.

Sigh. Lots of work.

---

### Post by Old Jimma on 2022-06-17
I mistyped someting:

The sever is pi**@**192.168.1.136

Table saw accident left me with a stumpy finger that causes mistyped words once in a while.

---

### Post by ActionParsnip on 2022-06-17
Is the issue now solved?

Make sure the "~/.ssh" folder on the remote server side is chmodded to 700 and the "authorized_keys" file is chmodded to 600

---

### Post by TheFu on 2022-06-17
> **Old Jimma said:**
>  
This makes me thing that I'm using the words "client" and "sever" incorrectly and what I mean as "client" is a server, and what I mean as "server" is a client.
 

Forget what YOU call the systems. It doesn't matter.  What ssh and sshd think are important.  The server runs sshd.  The client runs ssh, needs to use ssh-keygen and ssh-copy-id.

Typically, the ssh-client is the system you sit behind and the server is any other machine.
Of course, if you ssh into a remote machine first and want to ssh back out anywhere, then that remote system is the ssh client.

@ActionParsnip, this is handled by ssh-copy-id. It will create the directory if it doesn't exist too.

I hate USB storage.

Using a r-pi for backups is better than not having any backups, but far from ideal.  BTW, I'm loath to say this, but allowing ssh access to the backup storage on the back server is something malware likes.  It would be better if the r-pi "pulled" backups from each client, but that is much more complex logically, since it throws client and server for different aspects all over the place and when we add in sudo/root, it gets more complex since root on each side of the connection is different.  OTOH, every client that gets hacked can't corrupt/destroy the backups for all other systems.  Crawl first.

---

### Post by ActionParsnip on 2022-06-17
> **TheFu said:**
> 

@ActionParsnip, this is handled by ssh-copy-id. It will create the directory if it doesn't exist too.


Yes but there is an issue so things aren't going as planned, so it's good to check

---

### Post by TheFu on 2022-06-17
> **ActionParsnip said:**
> Yes but there is an issue so things aren't going as planned, so it's good to check

+1.  

My ssh troubleshooting article:  [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by Old Jimma on 2022-06-17
Ok. Will do.

---

### Post by Old Jimma on 2022-06-17
Mr ActionParsnip... no the problem is not solved.

I live on a farm and have alot of chores to do so that nothing dies. I'm going to take a shower and try out some of the things you've recommended. thanks.

---

### Post by TheFu on 2022-06-17
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)
[Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278)

Install SSH and Fail2ban (ssh is a meta packages on Ubuntu w/
  both the client and server stuff:
```
  $ sudo apt install ssh fail2ban
```
  # fail2ban defaults are preconfigured for ssh on 22/tcp.

Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```

Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```
 The "username" is optional and not needed if the same between the
 client machine and remote server.
 "remote" can be a DNS name, IP address, some manually setup lookup
 inside the /etc/hosts or configured in the ~/.ssh/config file.

Step 3: Test that ssh works.  ssh into the remote system, 
```
   $ ssh username@remote
```
 All ssh-based connections between the client and server should 
  now work just as easily.  ssh, sftp, scp, rsync, x2go,  rdiff-backup, sshfs, and 50 others regardless of the program.  

  Open a file manager like Caja, Thunar, whatever, Put 
    sftp://username@remote/ into the URL. Hit <enter>.
  An sftp connection should happen.  Some File Managers use ssh://
  instead.

Step 4: Lock down the sshd_config
```
   $ ssh username@remote
   $ sudoedit /etc/ssh/sshd_config
```
     Change line with:
  PasswordAuthentication yes
   to 
  PasswordAuthentication no

At the bottom of the file, add: 
  Match Address 192.168.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes
 
So it should look like this:
```
PasswordAuthentication no
Match Address 192.168.22.0/24,172.21.22.0/24,10.12.44.0/24
      PasswordAuthentication yes

```
Change the subnets to match yours. Those above are just examples. I
don't know if spaces on the address line matter or not.

If you got all this way and don't have ssh installed and working, well that sucks.

---

### Post by Old Jimma on 2022-06-17
I changed the permissions on both the server and the client to 777.

Still did not work.

---

### Post by The Cog on 2022-06-17
The permissions on directory /home/auggie/.ssh must be 700, and /home/auggie/.ssh/authorized-keys must be 600. Anything else and the server won't accept calls for that user. 
But you are getting connection refused. That's very basic, they aren't getting as far as discussing credentials. They're not even making the initial TCP connection.

First, on the server (the one that is supposed to be accepting an incoming ssh connection), use this command  to list all the listening incoming TCP ports, and make sure there is an entry like 0.0.0.0:22 or [::]:22. Let us know ant entries that end in ":22".
```
sudo ss -lntp
```
I'm wondering if that machine even has sshd running. It won't accept incoming connections unless sshd is installed and running.

---

### Post by TheFu on 2022-06-17
> **Old Jimma said:**
> I changed the permissions on both the server and the client to 777.

Still did not work.

No. No. No.  ssh won't work with the wrong permissions. It is security software and it cares.

To reset everything, run these commands on BOTH the client and the server:
```
sudo apt purge ssh
rm -rf ~/.ssh
```

If you run the exact commands in post #11 on the client and server, as specified, it works.  Just don't get the client and the server mixed up.  If you have already enabled a firewall on either system, you can disable it for now, get this working.  BTW, fail2ban will provide sufficient protection, so the only reason you'd need more is if you have a default DENY firewall rule. In that case, add a rule to allow ssh into the server.  ufw makes that easy.

---

### Post by web-user on 2022-06-18
You may also want to try to do the manual copy of .ssh/id_rsa.pub file (I don't remember exact destination) After this, restart SSH and retry logging in.

---

### Post by TheFu on 2022-06-18
> **web-user said:**
> You may also want to try to do the manual copy of .ssh/id_rsa.pub file (I don't remember exact destination) After this, restart SSH and retry logging in.

That's kinda the point of ssh-copy-id.  I've never seen it fail.  Also, there's no need to restart the sshd on the server after changing any user-files, but definitely would need to attempt a fresh connection from the client.  BTW, copying the .pub file over, but without appending it to the ~/.ssh/authorized_keys file wouldn't help.  And each public key needs to be on a separate line - no line wrapping allowed.  In the olden days, I'd use the X-buffer to copy/paste a new key to the end of the file, but the source key was usually 4-6 wrapped lines and the copy/paste would insert the NL, so I'd have to remember to remove those extra characters.  ssh-copy-id makes it bonehead, which is really good for me.

---

