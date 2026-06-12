---
title: "SSH after a VPN does not work"
date: 2016-01-08
forum: General Help
---

### Post by vishnugb on 2016-01-08
Hi!

I connect to a network using OpenVPN. I have established that the VPN has succeeded.

When I attempt to SSH though, I am not able to do so:

```
$ ssh [EMAIL="user1@172.16.11.139"]<user>@172.*.*.*[/EMAIL]
ssh: connect to host 172.*.*.* port 22: Network is unreachable
```

But then, I can ssh into my machine from other computers that are physically in the network.

Any guesses as to what the problem might be?

Thanks!

---

### Post by The Cog on 2016-01-08
Have you enabled IP forwarding in the VPN server? 
[http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

Also, check your firewalling within the network. 

Also, unless the VPN server is doing masquerading, the device you are trying to SSH into needs to know a correct route for forwarding its replies to the VPN client.

I know OpenVPN can pass SSH without difficulty - I do it nearly every day.

---

