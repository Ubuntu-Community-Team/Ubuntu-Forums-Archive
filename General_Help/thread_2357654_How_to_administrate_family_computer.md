---
title: "How to administrate family computer"
date: 2017-04-04
forum: General Help
---

### Post by nikperrakis on 2017-04-04
Hello,

I 'll be installing Ubuntu 16.04.2 on my old laptop and will be retiring it to some family members. I want to be able to remotely administer it if needed.

I 'm thinking the ability to ssh into it will be enough. But how do I do that? These are the steps I think I ll need to take:

[LIST]
[*]Enable and configure ssh-server in the laptop (but how do I do it?)
[*]Write an executable bash script that enables ssh-server and emails me internal and external IP of the laptop.
[/LIST]

I basically want to run  things like
```
sudo apt autoremove
# and
top
kill 12345

```
if something looks wrong on their end.

I m looking for free software solutions. If you have other solutions in mind I 'm interested.

Thanks,
Nik

---

### Post by QIII on 2017-04-04
Hello!

This is not as easy as 1, 2, 3 and Bob's your uncle.

Don't do anything yet.  Some light reading is in order first.

I would suggest starting with [this]("https://help.ubuntu.com/community/SSH") and [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring") in the Ubuntu documentation.  DigitalOcean always has great documentation, some of which you may find [here]("https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04") and [here]("https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2").  All of this *_is going to confuse you!_*  :) But it will give you some familiarity so that you can come back and ask more detailed questions.

Just as a rule:  NEVER allow root login.  You'll understand better as you go along.

Cheers!

---

### Post by bonestabone on 2017-04-04
What about using the default remote desktop viewer that comes with Ubuntu? Or do you need something less resource intensive.

---

### Post by TheFu on 2017-04-04
Welcome to the forums.

No need to pay for any software.  Everything you need is part of the normal Ubuntu/debian/fedora/SUSE repos.

I admin systems around the world only through ssh, but it took lots of effort to learn to do things only using the shell, no GUI.  Based on your questions, I suspect you don't have those skills at this point.  You'll also need to secure the ssh. Do not use passwords over the internet.  Only use ssh-keys for authentication.

A few things you'll need to do:
* Setup dynamic DNS for their WAN IP.  no-ip is one service [https://www.noip.com/free](https://www.noip.com/free) , but there are many others. Many routers will manage any WAN IP changes with the Dynamic DNS service. If not, you can install a daemon on the laptop to handle it form many routers. 
* setup static IPs on the LAN for the laptop.
* open a WAN port on their router - 60022 would be good. 
* forward the WAN 60022/TCP port to the laptop's ssh port. WAN 60022/tcp  --> LAN Laptop 22/tcp.
Get all of this working at your house first, so you know how to do it.  Just hope that their router isn't too different from yours.  Make a checklist.

Forget the bash script. That really shouldn't be necessary. The dynamic DNS stuff works well.

Just be aware that if the remote users change their networking, remove the static IP or do anything else like have to change the  network adapter used, then everything will break.  I should mention, using wifi for their LAN access could be troublesome, but it can work. Wired is 99% better than wifi for this, however.

And to secure the ssh stuff ... [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
Setting up key-based ssh: [http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication](http://blog.jdpfu.com/2011/07/14/easy-key-based-ssh-authentication)
Troubleshooting ssh connections: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by dragonfly41 on 2017-04-04
I'll just add another option.  I have good results using ngrok.

[http://dsernst.com/2015/02/17/ngrok-is-awesome/](http://dsernst.com/2015/02/17/ngrok-is-awesome/)

It is quite easy to use.

I use it with cloud based servers where I can point back to a demo url on my localhost laptop.

---

### Post by Autodave on 2017-04-04
"Teamviewer" is another alternative. Free program and very easy setup. I use it across 8 different computers to keep track of them and remotely control when necessary. Just google it and d-l file. I put the d-l on my USB and just have it with me all the time on my keyring in case I need to install it on another machine.

---

### Post by nikperrakis on 2017-04-04
Thanks for the replies, appreciate the help. I 'll study all of them to see what I ll do.

P.S. I used free as in speech not beer.

---

### Post by QIII on 2017-04-04
The best tools for this are free as in beer, anyway!

---

### Post by SeijiSensei on 2017-04-04
In the past I've managed this task by installing OpenVPN on the remote machine and configuring it as a client using a [static-key](http://openvpn.net/static.html) arrangement.  You would need to open a port on your router and use port forwarding to send the traffic from the remote to an OpenVPN server at your end.  Then when the remote machine boots up, it will set up the tunnel automatically and enable you to interact with the remote.  You can then use any method you want to run programs on the remote machine since it will be using the tunneled connection.

---

### Post by gordintoronto on 2017-04-04
+1 for Teamviewer. Free for personal use.

How old is the laptop? Will you give it to people who have only used Windows? Xubuntu or Lubuntu might be worth considering.

---

### Post by mastablasta on 2017-04-05
Teamviewer got hacked on massive scale last year.: [SIZE=2]https://arstechnica.com/security/2016/06/teamviewer-says-theres-no-evidence-of-2fa-bypass-in-mass-account-hack/
[/SIZE]
it Works great, but is not really that secure.

---

