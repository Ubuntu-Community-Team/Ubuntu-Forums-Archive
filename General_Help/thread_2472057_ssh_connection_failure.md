---
title: "ssh connection failure"
date: 2022-02-16
forum: General Help
---

### Post by Old Jimma on 2022-02-16
Hello Community:

I've had difficulty getting ssh to work between a host computer and one of my client computers. For example, ssh [email]client@client.ip[/email] does not work. I've queried the forum earlier about this and have receive excellent help trying to get ssh [email]client@client.ip[/email] and other work arrounds to work.... to no avail: the ssh connection from my host to that client fails.

Here is some info about the host computer:
[LIST]
[*]there are no commands in the firewall, ucf
[*]etc/hosts.deny has nothing in it: the ip of the host is not specified there.... nor is anything else
[*]
[/LIST]


There are a few web pages that discuss this issue: eg
[LIST]
[*][https://www.linux.com/topic/networking/4-reasons-why-ssh-connection-fails/](https://www.linux.com/topic/networking/4-reasons-why-ssh-connection-fails/)
[*][https://unix.stackexchange.com/questions/82277/ssh-not-working-from-one-specific-computer](https://unix.stackexchange.com/questions/82277/ssh-not-working-from-one-specific-computer)
[*]
[/LIST]

However, the discussion there is slightly over my head, and there are no explicit instructions on those pages that I can follow to test.

I should comment that this problem seemed to have happened immediately while my internet service provider (ATT) was digging holes in the ground and installing new internet fiber optics: the IP address of 2 of my computers changed.

What should I do?

Thanks,
Old Jimma

---

### Post by SeijiSensei on 2022-02-16
First, start by running "ssh -vvv remote_host" and see what errors pop up.

---

### Post by Old Jimma on 2022-02-16
Thank you for your reply, Seiji.

Here is what I think you asked for. From my server issued the command:

> 
 $ ssh -vvv client@192.161.1.124
[QUOTE]

and got these results... after the last line the 


[QUOTE]
OpenSSH_7.9p1 Raspbian-10+deb10u2+rpt1, OpenSSL 1.1.1d  10 Sep 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.161.1.124 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.161.1.124 [192.161.1.124] port 22.
debug1: connect to address 192.161.1.124 port 22: Connection timed out
ssh: connect to host 192.161.1.124 port 22: Connection timed out


Old Jimma

---

### Post by The Cog on 2022-02-16
Are the two computers on the same network, or do they have to go through routers, ISPs etc?
What does this command get you?
```
ip route get 192.161.1.124
```

---

### Post by TheFu on 2022-02-16
> **Old Jimma said:**
> Thank you for your reply, Seiji.

Here is what I think you asked for. From my server issued the command:

[QUOTE]
 $ ssh -vvv client@192.161.1.124
Old Jimma

I don't see the output (did you use code tags?), but it looks like sshd isn't running on the remote system. check that.

---

### Post by Old Jimma on 2022-02-16
Hello The Cog:

The 2 computers are on the same network... served by the same router.

Here is the output:

> 
$ ip route get 192.161.1.124
192.161.1.124 via 10.6.112.1 dev tun0 src 10.6.112.73 uid 1000 
    cache 



Thanks,
Old JImma

---

### Post by Old Jimma on 2022-02-16
Here is the output:


> 
$ ssh -vvv sandysmith@192.161.1.124
OpenSSH_7.9p1 Raspbian-10+deb10u2+rpt1, OpenSSL 1.1.1d  10 Sep 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.161.1.124 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.161.1.124 [192.161.1.124] port 22.
debug1: connect to address 192.161.1.124 port 22: Connection timed out
ssh: connect to host 192.161.1.124 port 22: Connection timed out



---

### Post by Old Jimma on 2022-02-16
Here is the output again:

$ ssh -vvv sandysmith@192.161.1.124
OpenSSH_7.9p1 Raspbian-10+deb10u2+rpt1, OpenSSL 1.1.1d  10 Sep 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.161.1.124 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.161.1.124 [192.161.1.124] port 22.
debug1: connect to address 192.161.1.124 port 22: Connection timed out
ssh: connect to host 192.161.1.124 port 22: Connection timed out

---

### Post by foxsquirrel on 2022-02-16
On the client

```
sudo apt install openssh-server
```

If I read your post correctly you are going from the server to the client so the client needs to listen for the incoming request.

Also if you have a Windows Box as a client you will have to turn openssh server on in the advanced apps.

---

### Post by Old Jimma on 2022-02-16
Thanks for your reply, Foxsqirrel:


It seems the openssh-server is open on the client:

> 
$ sudo apt install openssh-server
[sudo] password for sandysmith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version (1:8.2p1-4ubuntu0.4).
openssh-server set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



---

### Post by foxsquirrel on 2022-02-16
I am assuming you have done a ping?

---

### Post by foxsquirrel on 2022-02-16
```
sudo ufw status
```

on the client

---

### Post by The Cog on 2022-02-16
> **Old Jimma said:**
> Hello The Cog:

The 2 computers are on the same network... served by the same router.

Here is the output:

> $ ip route get 192.161.1.124
192.161.1.124 via 10.6.112.1 dev tun0 src 10.6.112.73 uid 1000
cache 

Thanks,
Old JImma
That doesn't look as though they are on the same network. It's trying to go via a VPN connection. 
* Were you aware of the VPN? 
* Can we see the output from these two please?
```
ip address
ip route
```

---

### Post by TheFu on 2022-02-16
Having sshd installed doesn't mean it is running. Please verify that on the 'server', which ever system that is.

In my world, I have sshd running on every box because it is just too convenient for ssh, scp, sftp, rsync, sshfs, and backups.  None of those things will work without it.  On ubuntu systems, there is a metapackage "ssh" which includes the client AND the server parts for openssh.

To install, my normal command is:
```
$ sudo apt install ssh fail2fan
```

On all ubuntu systems, that's it. The firewall isn't running by default.  Of course, if you are using any funky routing or VPN or there is a firewall between the 2 systems, you'll need to address that yourself. It isn't part of ssh.

Next, I setup ssh-keys from the client to the server. If my client already has a public ssh key, but I'm connecting to the a customer's systems, then I'll generate a new ssh-key just for that customer's connections.

If I just brought up a new box, say a 22.04 alpha test server, then I'll just push my existing, default, ssh-key to it.
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386) has more, but the short answers for key creation and pushing to a remote system are:

Step 1:  Run on the client as the normal user:
```
   $ ssh-keygen -t ed25519
```
Step 2:  Run from the client to the server:
```
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```

You can force the public/private key files to have a different name, just use the **-i** option on all ssh* commands.  Don't forget to put the keys file into your ~/.ssh/config file for each different server **IFF** to choose a non-default name.  

If we don't specify the type of key in the keygen command, we'll get a 2K RSA key which may not be strong enough. The cipher to use is up to you, but ed25519 is considered highly secure, very hard to crack, harder than a 4K RSA key right now and best of all, the id_ed25519 key will be used automatically. It is in the list of keys to be used for all ssh-based commands.

Setting up a ~/.ssh/config file ... means even if you don't have DNS, you'll never need to remember a username or IP address or non-standard port or which key to use for any remote machine. I think [Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](Https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278) goes into that.
It is common for me to have multiple 'config' entries into the same system
a) for when I'm on the LAN and the box is too new to be in DNS yet. Normal port, my LAN username.
b) for when I'm on the internet. This will need to use a non-standard port. The WAN router does port-translation  into the jump server, then into the requested server.
c) for when I need to connect with a different userid. This could be a test account, deployment account for DevOPS stuff or a root-equiv account for backups that get pulled. The root-equiv account can only originate from a backup server. No others.

Hope this is helpful.

---

### Post by Old Jimma on 2022-02-17
ssh -vvv sandysmith@192.161.1.124
OpenSSH_7.9p1 Raspbian-10+deb10u2+rpt1, OpenSSL 1.1.1d 10 Sep 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolve_canonicalize: hostname 192.161.1.124 is address
debug2: ssh_connect_direct
debug1: Connecting to 192.161.1.124 [192.161.1.124] port 22.
debug1: connect to address 192.161.1.124 port 22: Connection timed out
ssh: connect to host 192.161.1.124 port 22: Connection timed out

---

### Post by Old Jimma on 2022-02-17
Hi THe Fu:

Just saw your post today (2/17 9pm). 

I'll work on it.

Thanks,
Old

---

### Post by Old Jimma on 2022-02-17
Hi The Fu:

Here is some context: ssh was working fine on all of my computers, and the raspberry pi that you recommended for doing rsync to back up all of my computers worked great. 

All of my computers are ubuntu 20.04 except for the pi that used PI OS (raspian)... ubuntu work 20.04.03 worked very, very poorly... unreliably... on the pi.


Then one day, ATT started digging in the neighborhood, and doing things they said would help our computers.

That was the day 2 of my computers changed IP addresses.

And, that's the second time in 6 months when ATT was digging holes in our yard that IP addresses changed on my computers.

Changing IP addresses wreaks havoc. NFS and ssh doesn't work any more because IP addresses changed. But I think their "improvements" meant more than just changing IP addresses for me... and not for the good.

A further thing I'm gong to do is to connect the computer with the problems directly to my network with a cat6 cable, instead of using wifi. All of my computers that are directly connected to my network by a cat6 cable work well.

If a cat6 cable works, that means I have to find a way to run 200' of cable in a discrete way rather than have it run up (and down) stairs.

I'm going to try out your suggestion. I appreciate your work and thought.

Sincerely,
OLD

---

### Post by TheFu on 2022-02-17
Why would the IP address change on your LAN?  Don't you set all the systems with static IPs?  If you don't, it is 100% your fault, not AT&T.  
Not having static IPs on your LAN for anything that runs a network service is your fault.

---

### Post by Old Jimma on 2022-02-19
Hello The Fu:

I've recently come to the understanding is that when my internet provider "does things" IP addresses can change.

In the past 2 months, they've "done things" twice.

The Fu, I am not a computer scientist. I'm just a retired scientist who specialized in another area that used computers extensively (including super computers), but didn't ever become engaged in managing them, or maintaining them. 

In retirement, almost all of my time is consumed by composing for multi-piece jazz bands using musescore, in between times when I'm not so ill that I can't do anything.

Of course everything is my responsibility. 

Because of the "adjustments" my internet service provider has made in the past 3  months,  I've gained the understanding that all of the computers on my network need fixed IP addresses. You may recall responding to a forums query several months ago when I asked about having a subnet... I had just begun to understand the importance that you have described then.

I'm just an old man now, and what I've learned better than anything else is that the only way I learn is through my failures that invariably is caused by ignorance. 

I'm doing my best and have been grateful for the forums to point me in the right direction.... 16 years now.

Thanks for providing excellent advice, The Fu.

Old Jimma

---

### Post by TheFu on 2022-02-19
Many home routers have something called a "dhcp reservation". This can work to keep IPs static and centrally managed as a starting point, then you can slowly work through each system and setup on-the-system a static IP.

The trick is that reserved IPs from DHCP need to be outside the dynamic IPs range that the DHCP server provides.

So, if you want static IPs to be from .1 - .99, then setup the dhcp range in the DHCP server (which can be your router or another DHCP server on the network), to .200-.254.  Don't let them overlap.  I wrote a blog article about this last decade. I don't think DHCP reservation setup is nearly as hard now as it was back then.  [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

---

### Post by Old Jimma on 2022-02-22
Hello Ubuntanians:

In this thread, I reported an "ssh failure."

And, indeed it was... and was caused by me.

The rule is:** if you change the ssh keys on either the server or the client so that the keys are no longer identical, the server and client will not be able to talk to each other using ssh.**

The way I solved this problem was to first:
[LIST]
[*]back up the files on the client,
[*]reinstall Ubuntu on the client, 
[*]use **ssh-copy-id [email]client.machine@client.ip[/email] ** to copy the keys on the server to the client again, and then
[*]restore the files on the client.
[*]
[/LIST]



When you use **ssh-copy-id [email]client.machine@client.ip[/email] ** to copy the keys on the server to the client again It is entirely possible that you will get a scarry message about a man in middle attack. Just read the entire message, and follow the instructions. You'll be guided to run a command that will resolve the problem.

Finally, use the **ssh-copy-id** command to copy the ssh keys from the server to the client, again. It will work after you've read the scarry message, followed its instructions, and resolved that matter.

This method has worked well for me.

Finally, think about what you did that resulted in different keys on the server and the client, and try to avoid doing it again. It took me a few failures to realize what I had done.

Old JImma

---

### Post by TheFu on 2022-02-22
[COLOR="#FF0000"]client.machine[/COLOR]@client.ip - that isn't correct.
[COLOR="#008000"]username@client-ip[/COLOR] is probably what you meant.

Also, you can setup a different ssh-key for each system connection, if you prefer. Just name the file different when using **ssh-keygen**.  The manpage is pretty clear.  But you'll either need to specify the key to be used with every ssh-based connection or you'll need to setup a ~/.ssh/config file to spell out the key file to be used for that other machine.

ssh-keys have a pair of files.  The private key and the public key.  Public keys have a .pub suffix.  Feel free to share the public key(s), but never, ever, share the private key(s).  These can be moved, copied, between systems as you like. ssh connections do some minor validation that a public key is matched to the client requesting to use it.  That can be a hostname or an IP address or that security can be disabled (bad idea). The security is usually controls in the sshd_config file on the remote system, under administrative control.

---

### Post by Old Jimma on 2022-02-23
Yes, thank you, The Fu.

Also, thanks for indicating how one can set up a different ssh-key for each system connection, and the description about pub and private keys.

That flexibility will enable ssh to be even more useful.

If nobody objects, I'll close this thread as being solved.

Old JImma

---

### Post by Old Jimma on 2022-02-23
I have to write a 2-chorus solo for guitar to day for Alone Together. I'll be getting back to you soon on setting up a static IPs. I saw an Ubuntu web page that enables me to use ubuntu gui features to do it, but I don't understand some of the "inputs." 

Ignorance is not bliss.

---

### Post by MAFoElffen on 2022-02-24
Two notes:
You do not need to reinstall Ubuntu just to replace/change ssh keys.
When asked if he could ping the target, I never saw those results... Why was that asked? Because the Op said both were on the same network and were serviced by same router.

Here is what that statement meant to me and what question it brought up. One's IP was on a network of 10.0.0.0. The other on a network of 168.192.0.0. They are not the same Network ID, but connected on the same locally physically, if they were serviced by the same router, then maybe a route was set up to route between the two network ID's. A ping would have verified that.

I'm not involved with this, but reading this, that is what I see, and what it brings to my mind.

---

