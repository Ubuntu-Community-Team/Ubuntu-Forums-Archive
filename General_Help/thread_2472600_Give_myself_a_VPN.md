---
title: "Give myself a VPN"
date: 2022-03-05
forum: General Help
---

### Post by Phil Binner on 2022-03-05
I have a few computers and a very simple network, running from an Xubuntu server.  Thanks to all who helped me to set this up.

I travel regularly and would like to be able to disguise this fact by connecting to the internet through my home server by VPN.  I have not the slightest idea how to do this; not even the basic concepts that would allow me to ask the right questions.  Can anyone help with this please.

---

### Post by TheFu on 2022-03-05
Do you have a static IP at home?  If your public IP(s) change all the time, that makes running any service at home more difficult.
Do you have a domain registrar? If you don't, you'll need to access home using an IP, not a domain-name.
Is your upstream bandwidth sufficient?  VPNs use more bandwidth and the upstream tends to be a limiting factor. Typically, DSL doesn't provide enough, but almost all cable and fibre connections do.
Does the contract with your ISP allow running a VPN server?  Many residential contracts have "no server" clauses. For your personal convenience, I doubt anyone at the ISP would notice or care, but ... a business ISP contract is usually required to be 100% within the terms of use.
Does your ISP give out routable IP addresses?  If the WAN side of your connection only gets a 192 or 172 or 10 IP address, then you won't be able to contact your house from remote locations. Most cell-data connections do this. There are ways around it, but ... it is much more complex and probably not something a beginner should attempt.
How strong is your networking knowledge.  Can you enter an iptables rule to forward a port in and out?
Do you have any idea about security?  For example, are you already using ssh when away from home with ssh-keys?

Running a VPN server yourself is harder than using ssh, but ssh can accomplish nearly everything a VPN can.  The only reason I have a VPN server at home is for Android client access. When I'm on a Linux laptop, using ssh and ssh-tunnels is far easier.

There are a number of different VPNs that you can run. Each with pros and cons.  
There are the complex openvpn-based solutions. **OpenVPN** becomes complex, quickly. But openvpn has been around a long time and there are lots and lots of guides for almost every configuration. That's good and bad. Finding a guide isn't easy, at least not for what I needed.
**Wireguard** is a newer vpn that has much lower overhead, but it isn't a proven. When it comes to security, nothing replaces time-in-the-field.
There are mesh VPNs like **nebula** or **tinc** which tend to be easier for clients, but the server still needs to be on the public internet, with public IP and accessible by all the clients.

Do some research.  Ars Technica has a few articles on each of these things.  I'd recommend that you:
[LIST]
[*]do not run a vpn on your router. A misconfiguration would have your router pwn'd. Not good.
[*]do not run the vpn on a system used for any other purpose. VPN needs to be a single-purpose system. A virtual machine is fine, but not containers.
[/LIST]

Consider setting up a VPN server at a VPS somewhere. That way when you screw it up, your home network isn't completely hacked.  Setting up a VPN on an VPS should take less than 5 minutes, once you know what you are doing. This solves all sorts of other issues too. 

Of course, if you still want to access files and systems at your house, use ssh. Then you can use **sftp** from any Linux file manager, **ssh** to have a remote terminal on any system inside your home LAN, and if you setup **x2go**, you'll have a desktop inside your LAN for remote access without risking any sensitive data to the outside world.  x2go works over ssh. It is part of the NX protocol used.

There are probably 20 other commonly used tools that are based on ssh, like sshfs, and rsync for accessing other stuff.  If you have some internal websites inside your HOME lan, you can use ssh as a browser SOCKS5 proxy too.  I've posted a script here for that purpose a few times. I access a number of my internal websites using this. Works very well, actually.

---

### Post by QIII on 2022-03-05
TheFu (a supremely knowledgeable member of our community, so listen carefully!) has beaten me to this question, which you may want to address before you even go about trying to figure out the "how":

> Does the contract with your ISP allow running a VPN server? 

---

### Post by Phil Binner on 2022-03-07
I know what my public IP address is now.  How do I find out if that is static.

I do not have a domain registrar.

My connection is fibre optic with the final section by copper.  It is fast but not perfect.  On th other hand I live in a village so competition al;lows me to get better download speeds that most urban systems.  My ISP has assured me that my connection is not throttled back.

I don't know what my contract says, but I do not intend anyone bet me to use this.

Currently my IP address starts 46.69.   Does this answer your question.

My networking knowledge is poor.

I have currently not set up Secure Shell, and I do not access my server remotely.

All I am trying to accomplish is to hide the fact that I am away from home without using a VPN which will be recognised by services which I have paid for.  I do not want the services I paid for to be withheld from me; the perpetual battle of theft and counter theft.  If I can accomplish that by using SSH then I will be very happy to do that.

---

### Post by dragonfly41 on 2022-03-07
I admit that I am puzzled.
You want to go off on some trips and leave your home unattended?
You want to fool some parties into believing that you are still at home using your PC's and server? And so avoid being burgled (you mention "theft and countertheft").

What pattern of usage do you hope to emulate in this unattended mode?
Is it just to generate false network traffic to and from your server?
But who are you hoping to fool?

Just trying to understand.

---

### Post by TheFu on 2022-03-07
I'd bet it is more about being able to access entertainment when way from home, for things that are perfectly legal in the location of the home, but some services geo-lock.  Some people just want their netflix.

Assume you do not have a static IP if you aren't paying for it. They are typically extra for IPv4 addresses.  If you have IPv6, you may have a static subnet. Not all ISPs do IPv6 stuff well and I don't know enough to provide any guidance.

My recommendation is to setup and secure ssh for access when away from home as your first step.  That effort will help you learn the networking aspects and securing ssh is a well-worn task with plenty of help on the internet.  After you get that working, the exact same network issues happen when trying to allow a VPN ... but you'll need to add in the extra complexities that a VPN includes.  Definitely get ssh working and learn to use it for 
* ssh
* sftp
* sshfs
* any NX remote desktop
* ssh tunnels
* rsync
After you get those working, you'll be ready to move onto VPN stuff.  sshd doesn't need a dedicated system, but I'd strongly - very strongly - recommend that any VPN is setup on a separate, dedicated, device that doesn't do anything else.

---

### Post by Phil Binner on 2022-03-08
Yes, that is precisely what I want.  I contribute heavily to the entertainment industry, not just Netflix but also Sky, Amazon, and a UK TV License, which goes to pay for the BBC.  None of these things are available when I'm away from home, and I can imagine how they'd react to my asking for a refund for 6 weeks a year.  All of these organisations are able to detect my VPN and shut down the service.   I regard that to be theft.

From what you have said I suspect that setting up my own VPN server is a no go, and I certainly don't have unlimited time to start a new learning curve just now.  I will take what you have said about the secure shell on board, however, and look at articles on that as I get some time.

In the meantime if anyone has any simpler suggestions I would be pleased to hear them.  Otherwise I'll shut this down in a couple of days.

---

### Post by dragonfly41 on 2022-03-08
Now that I understand that it is for viewing entertainment from afar perhaps try ngrok.

[https://ngrok.com/](https://ngrok.com/)

ngrok gives public access through tunnel to localhost server (your Netflix service etc.?).
Would that be blocked by your service provider?

---

### Post by ActionParsnip on 2022-03-08
Could just use an SSH tunnel and set that as the proxy on the client once connected. SSH home to the server and then set localhost:port as your proxy in your web browser.
[https://www.howtogeek.com/168145/how-to-use-ssh-tunneling/#:~:text=The%20SSH%20client%20will%20create,connection%20to%20a%20remote%20location](https://www.howtogeek.com/168145/how-to-use-ssh-tunneling/#:~:text=The%20SSH%20client%20will%20create,connection%20to%20a%20remote%20location).

Dead easy. No VPN faff.

---

### Post by TheFu on 2022-03-08
> **ActionParsnip said:**
> Could just use an SSH tunnel and set that as the proxy on the client once connected. SSH home to the server and then set localhost:port as your proxy in your web browser.
[https://www.howtogeek.com/168145/how-to-use-ssh-tunneling/#:~:text=The%20SSH%20client%20will%20create,connection%20to%20a%20remote%20location](https://www.howtogeek.com/168145/how-to-use-ssh-tunneling/#:~:text=The%20SSH%20client%20will%20create,connection%20to%20a%20remote%20location).

Dead easy. No VPN faff.

There are some caveats with this, but yes, this is what I'd use before going full VPN.  There are well-meaning people who post how to setup VPN servers out there.  Out of all of them, PiVPN is probably the easiest with the least chance of security failure for someone without much networking knowledge.  VPN servers aren't 1-click installs. They REQUIRE network knowledge and skills.

But if you just want a secure web connection to appear to come from your HOME, the using an ssh tunnel as a SOCKS5 proxy to a local browser is the easiest to use. Oddly, I find using chromium as the browser easier than using Firefox because setting up the proxy location can be passed in as an option. With firefox, we have to mess around with profiles which I find offensive.

---

