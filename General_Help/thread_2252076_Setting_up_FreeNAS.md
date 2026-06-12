---
title: "Setting up FreeNAS"
date: 2014-11-08
forum: General Help
---

### Post by victor47 on 2014-11-08
Hey guys I'm very new to Linux, I thought to switch over and try things out to see if I liked it, However I need help on a few things because I have no idea on how to do it or get started so if anyone know how to please help:)

Ok I installed Ubuntu 14.04 on an PE2900 server and I want to have a certain amount of the space available as a nas web access server I can access from anywhere that has internet connection?? I found a few tips on FreeNAS with Webmin but Its confusing and I don't want to ruin and have to start all over?

could any on Help me by showing me how to setup a NAS server on ubuntu that I can set a certain amount of memory for it and edit at any time and also access it via web browser from anywhere???

---

### Post by TheFu on 2014-11-09
So - allowing web-based access to your storage is really dangerous.
OTOH, if you setup an ssh-server, then you can access the storage from anywhere in the world, securely, using sftp.  sftp has clients for every OS.

BTW  FreeNAS is BSD based, not Linux.

If you want a NAS that access really, really, really, needs to be limited to the LAN, not over the internet (except through ssh or openvpn).

Of course, this is just my advice. You can do what you want using DAV (DAV has a long history of being hacked).  If you insist on using a web-only interface, please, please only access storage though openvpn. Then you can feel safe using almost any method you like - owncloud or seafile.  Those are probably mostly what you want if a personal dropbox server is the end goal. I use rsync+ssh myself.

---

### Post by victor47 on 2014-11-09
Could you show me how to make a SFTP on ubuntu 14.4, maybe a video?? link I'm looking to make a few people have access to it as well but id be admin??

---

### Post by nerdtron on 2014-11-09
> **victor47 said:**
> Could you show me how to make a SFTP on ubuntu 14.4, maybe a video?? link I'm looking to make a few people have access to it as well but id be admin??

If you can ssh into the server (just install the openssh-server package) from the outside network, people will be able to sftp too.
Just open FileZilla, set the IP address, provide username and password and port 22. Now you'll be able to upload/download to the server.

---

### Post by TheFu on 2014-11-09
@nerdtron - while technically correct, this is a good way to get hacked in the first 24 hrs. I know that you know this.
All of this is off the top of my head .... 
* ssh is part of scp, ssh, sftp - when you install the openssh-server, you get servers for all of those. These map exactly to zero-security tools rcp, rsh, and ftp. None of those should be used today or for the last 15 years inside ANY network for any reason ... ok - there are small situations where it would be fine, I suppose.
* ssh is how people hope from system to system to system around the world and have tremendous control over systems. I manage about 30 systems using ssh access only ... with tools that work over ssh.
* There are ssh clients for almost every OS. It is best to avoid anything that is not based on the openssh team's release. Forget the pretty GUIs.  
* Be very careful who you allow to ssh into any machine. They have local access and you should be paranoid since they just got onto your internal network and can launch attacks from **inside** to every other device now.  This also means they can run any program remote, and send all the traffic through your network before coming to theirs.  ssh can setup a vpn to make traffic look like it comes from your system. If you are paying for the internet connection, find. If you are using someone else's internet (mom/dads) please don't allow others. They will probably abuse your trust and break laws. They can launch fairly heavy hacking attacks around the world over this. You've been warned.
* use **sftp-only** settings for remote users. This is inside the sshd_config file. This will block them from using ssh and scp. Probably a smart idea.
* sftp uses normal userids on the system for file/directory permissions. This is extremely important. I cannot stress this enough.  Anyone you allow sftp access to the server, by default, gets the permissions of their userid everywhere on the system.  You need to have a strong understanding of file/directory permissions. If you don't, they may be able to pwn your box. 
* For all remote access - do not use passwords. Use ssh keys created by ssh-keygen. Larger is better than smaller. Do not accept the defaults.  ssh keys are one of those things which are both more secure AND more convenient than other options. How often does that happen?  Enforce key-only authentication in the sshd_config file - 
* Block persistent hacking attemtps - use either **denyhosts** or **fail2ban**. There are packages for ubuntu for both. Use one, not both.
[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has more details.
Sorry - that's all I have time for now.

---

