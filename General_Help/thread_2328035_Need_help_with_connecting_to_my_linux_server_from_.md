---
title: "Need help with connecting to my linux server from windows"
date: 2016-06-16
forum: General Help
---

### Post by clarkycal on 2016-06-16
Hello ubuntu community,
i connect to my linux server using the application called "WinSCP"
BUT to connect i use the IP: 192.168.0.17 (it works fine btw)
i want my friend to connect but what ip do i give him to connect, If that makes sense? because he can't use the local one (192.168.0.17)
he needs one such as a public one?
Thank you, all help is appreciated.

---

### Post by TheFu on 2016-06-17
Welcome to the forums.

An overview:

You need to setup the system for external ssh access.  Lots of how-tos for this exist. Generally, they include
a) dynamic DNS service (ddns) - many home routers have a pull-down list of supported services. no-ip is popular.
b) static IP on your internal sftp server - can either manually set this or can have the router use ¨dhcp reservations¨ to give the machine the same internal IP, always.
c) modify the router to forward the inbound port to the server port 22/tcp. May want to use port translation so the default port, 22/tcp, is NOT used on the public WAN connection.
d) Secure the sftp/ssh service - fail2ban is the minimal thing to be done. Really shouldn´t use passwords over the internet at all. ssh-keys would be better and locking down the allowed source IP(s) of your friend´s connection would be best.  Don´t want people from the big-evil-internet having unlimited attempts to hack in.

After you do this once, it is easy.  The first time, it is helpful to draw a picture with all the network parts on it, label all the IP addresses and ports used. This will become like a check list for all the things in the line between him and you which need to be opened.

You may want to disable ssh access by his account, so he can only use sftp and only to specific directories you want.  the sshd_config has settings for that which can be tweaked per-userid.

---

### Post by clarkycal on 2016-06-17
TheFu i thank you, most helpful answer someone has given me!
Thanks again,

---

### Post by TheFu on 2016-06-17
A few links ... as I help folks do this weekly at my LUG:
* [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
* [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)
* [http://lifehacker.com/5831841/know-your-network-lesson-4-accessing-your-home-computers-from-anywhere](http://lifehacker.com/5831841/know-your-network-lesson-4-accessing-your-home-computers-from-anywhere)

Don't use the DMZ option, ever. Only open the 1 port you decide to allow on the WAN. Use a non-standard, high port, to prevent the riff-raff from unlimited attacks.

ssh can do much more than people realize. For the lurkers ... [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

