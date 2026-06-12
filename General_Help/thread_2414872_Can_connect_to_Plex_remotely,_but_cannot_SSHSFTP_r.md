---
title: "Can connect to Plex remotely, but cannot SSH/SFTP remotely"
date: 2019-03-16
forum: General Help
---

### Post by ejach2000 on 2019-03-16
Hello,
I am running Ubuntu 18.04 as a media server back home.
I am currently away from my house for a few months, so I decided to set up a Plex server before I left.
I had a lot of trouble setting the Plex server to be accessed remotely, but I finally got it to work.
Now that I am away from home, I can use Plex just fine, but I cannot SSH or SFTP to my server at all.
My UFW permissions are not the issue, but I can attempt to get them upon request.
My ports are forwarded correctly, but I can get them upon request.
I am not sure what else to provide since I cannot access my server right now,
but any additional information can be provided upon request.
Thanks!

---

### Post by TheFu on 2019-03-16
Please provide proof for all claims.
* ufw is open
* port forwards are working
* ssh server is enabled and running
* userid has ssh authority

How do you access plex?  I use an ssh tunnel.  I do not have any plex user account. It works fine from almost anywhere, I just need to manually set the video bitrate depending on my current location. I've also used openvpn to tunnel into my LAN and access plex.  This works using the web interface.  Normal DLNA clients do not work if they aren't on the same LAN.

I do not use any official plex clients.

---

### Post by ejach2000 on 2019-03-16
> **TheFu said:**
> Please provide proof for all claims.
* ufw is open
* port forwards are working
* ssh server is enabled and running
* userid has ssh authority

How do you access plex?  I use an ssh tunnel.  I do not have any plex user account. It works fine from almost anywhere, I just need to manually set the video bitrate depending on my current location. I've also used openvpn to tunnel into my LAN and access plex.  This works using the web interface.  Normal DLNA clients do not work if they aren't on the same LAN.

I do not use any official plex clients.

Due to not being able to connect to the server remotely, I need to set up a time with a family member back home to do a join.me session on my home network. I will update you with everything once I have it.
In response to your second question, I access plex through the official plex clients.
Thanks for the quick reply!

---

### Post by TheFu on 2019-03-16
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) should help. Be certain to validate the server assumptions, like that it has a static IP on the LAN.

---

