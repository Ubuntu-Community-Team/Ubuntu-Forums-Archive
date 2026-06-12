---
title: "IP Network/Gateway Change"
date: 2019-05-18
forum: General Help
---

### Post by agriffs on 2019-05-18
[COLOR=#242729][FONT=Arial]Let me start by saying I am a complete novice with very little networking knowledge.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have set up a VPN via a guide and everything is working fine, however, I would like for the IP routing or gateway to stay permanently as my current solution is only temporary.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Basically I used the command[/FONT][/COLOR]
> ip route | grep default

[COLOR=#242729][FONT=Arial]and it shows[/FONT][/COLOR]
> default via 206.189.112.1 dev eth0 onlink

[COLOR=#242729][FONT=Arial]The guide I am using requires it to be[/FONT][/COLOR]
> default via 206.189.112.1 dev eth0 proto static

[COLOR=#242729][FONT=Arial]Which I managed a workaround by using replacing the above with[/FONT][/COLOR]
> sudo ip route add default via 206.189.112.1 dev eth0 **proto static**

[COLOR=#242729][FONT=Arial]I was wondering how I could change it from "onlink" to "proto static" permanently.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by TheFu on 2019-05-18
I'll ask some questions, so the information is available to someone who can actually help.  While I've been running VPNs since the mid-1990s, I've never need to know too many details. Most were commercial for thousands of concurrent users.

Anyway, some questions: 

There are many ways, but the best depends on the specific version of Ubuntu you are running and whether it is server or some desktop. Please provide that information.

It also depends on the actual VPN server being used. Please provide that information.

FYI, routes are normally pushed by the VPN server and I suspect you aren't running the server, just the client.  On an openvpn server, there is an option for the config file:```

       --iproute cmd
              Set alternate command to execute  instead  of  default  iproute2
              command.   May  be  used in order to execute OpenVPN in unprivi&#8208;
              leged environment.
...
       --route network/IP [netmask] [gateway] [metric]
              Add route to routing  table  after  connection  is  established.
              Multiple  routes can be specified.  Routes will be automatically
              torn down in reverse order prior to TUN/TAP device close.

              This option is intended as a convenience proxy for the  route(8)
              shell  command, while at the same time providing portable seman&#8208;
              tics across OpenVPN's platform space.

              netmask default -- 255.255.255.255
...

```. These can push the necessary routes to the specific clients.  There are many other config options related to routing. Like 10 more. This is for openvpn. If you are using a different VPN, things will be different.

A link to the guide might help someone help you too.  Sometimes guides are great and other times they leave out tiny details which make the VPN not actually secure.

---

### Post by agriffs on 2019-05-18
The guide I have been following is as follows - [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04)

As shown above, I am indeed running an OpenVPN server on Ubuntu 16.04.6.

I will mention that I am not at all familiar with the networking sides of things. I don't quite understand the difference between "onlink" and "proto static", however, manually changing it has worked for me so far. I was just wondering if there is a better way to make this change permanent, as a server restart only resets it back to "onlink", requiring me to manually change it again and also needing to restart the OpenVPN service to get it running again.

---

### Post by TheFu on 2019-05-19
That link is for 18.04 - at least the linked version, not 16.04. Did I miss something? 

There are HUGE differences in the networking subsystems between 16.04 and 18.04.  Canonical decided to swap out the methods we've been using for 20+ yrs with something completely new, netplan, that appears to still have issues with non-trivial networks, like VPNs, over a year after release.  Which ubuntu release is correct?  
 
In 16.04, if you always want the VPN active, you could use the **post-up** option in the interfaces file to run a script. That script would start the VPN client and modify the routes.  It all runs as root, so no need for sudo.  The manpage for interfaces as the details.```

       post-up command
              Run  command  after  bringing the interface up.  If this command
              fails then ifup aborts, refraining from marking the interface as
              configured  (even  though it has really been configured), prints
              an error message, and exits with status 0.   This  behavior  may
              change in the future.
```
And you probably want to remove the route, then bring the VPN down cleanly, in the pre-down command:```

       pre-down command
              Run  command  before taking the interface down.  If this command
              fails then ifdown aborts, marks the  interface  as  deconfigured
              (even  though  it  has  not really been deconfigured), and exits
              with status 0.  This behavior may change in the future.
```
Having a clean start and stop is important so other commonly needed things work correctly.

Hopefully, netplan in 18.04 has some methods to accomplish the same things. IDK. I'll probably be able to avoid knowing it for another year.

One last question.  Is this the client-side or the server-side of the VPN? It isn't clear.

---

