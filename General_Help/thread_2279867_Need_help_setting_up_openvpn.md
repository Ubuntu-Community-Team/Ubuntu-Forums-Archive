---
title: "Need help setting up openvpn"
date: 2015-05-26
forum: General Help
---

### Post by Azdour on 2015-05-26
Hi all,

Before the weekend I set up a test server on our local network and installed openvpn.

It all went well and I could ping the server from my client when connected.

Then I hit the first problem.  When I ssh'd into the server using the 10.8.0.1 address it asked for a password.  I entered the usual password that I had used many times before openvpn was installed and it kept saying incorrect.

So I played with the server.conf and earlier today I got to the point where I could no longer ping the server from the client.  So I rolled back the server.conf and started again.

I followed the instructions on this site to set up the server (I used the gunzip of the server.con to roll back the server.conf, and made the same changes again):

[https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04)

Now I am still unable to ping the server.  I have no firewall or any iptables rules that I am aware of.

Any help with my issues would be greatly appreciated with:

1. Cannot ping the openvpn server on 10.8.0.1 from my client on the same network
2. Once I get the first issue sorted why would it not accept my password for ssh - before openvpn ssh worked fine

---

### Post by SeijiSensei on 2015-05-26
OpenVPN should have no effect on your ability to log in with your password.  Can you SSH to the server directly and log in?

If all you're trying to do is set up a simple point-to-point tunnel with OpenVPN, I recommend following the procedure described here:  [https://openvpn.net/static.html](https://openvpn.net/static.html)

---

### Post by Azdour on 2015-05-26
Thanks for the quick reply.  I can SSH into the server with its normal IP address.

My main problem is that I can no longer ping the server using the 10.8.0.1 so I cannot even test SSH any more.

Going to take a look through the guide you posted.

---

### Post by Azdour on 2015-05-26
Ok, using the guide at the link you provided I was able to narrow down the issue to comp-lzo.  I had not told the client to use it :)

Now I can ping the server and ssh works.  Thanks.

---

