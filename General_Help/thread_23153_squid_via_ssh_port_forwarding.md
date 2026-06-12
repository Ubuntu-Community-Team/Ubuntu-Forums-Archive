---
title: "squid via ssh port forwarding"
date: 2005-03-31
forum: General Help
---

### Post by silicon.pyro on 2005-03-31
I am looking to set up a squid proxy on my box at home to use as a secure proxy while browsing wirelessly from public hotspots.

I have installed and sucessfully used squid directly from my laptop.
I have used port forwarding to connect localhost/53128 on my laptop to my server at the default /3128 port.

Though I can shield myself from the prying eyes, my problem is that the server still accepts non-ssh connections to the squid port, effectivlely allowing anybody to use my proxy.  Not that I'm opposed to sharing, just that my ISP is :).

I had the following ideas, but none are ideal:
1) use squid authentication (but NTLM isn't secure)
2) use squid mac-address filtering (too easy to spoof)
3) use squid IP address filtering (I never know what my IP will be on a public WAP)

Of course in situation 1) the insucurity is made a little better by the fact that I would always be using ssh tunneling to connect, sheilding my password and username from the world, but this still isn't ideal.

I have been using Ubuntu for months now, and I'm truly impressed.  I am new to linux firewalls and squid configs and I can't seem to think of a way to block non-ssh access to the 3128 port.

Any comments/suggestions would be greatly appreciated?

---

### Post by raamdev on 2005-04-30
I also use Squid to securely browse the web from wireless hotspots by SSH'ing into my Squid server, forwarding port 3128 to my laptop, and then setting Firefox to use 127.0.0.1:3128 as the proxy. 

Regarding your issue with not allowing non-ssh users (anyone) to access your Squid server: Do you have a router infront of your Squid server? I have a Linksys router infront of my Squid server and I only forward port 22 to my server (for SSH). If you don't forward port 3128 then no one can access the Squid proxy without first SSH'ing into the server and forwarding the port to their local computer. 

If you don't currently have a router, and your Squid server is directly connected to your broadband connection, then I highly reccomend you invest $40 and get yourself a Linksys router. Putting your internal network behind a router allows for some simple protection. The only ports that will be accessable from the internet are the ones you specificly forward on the router. 

Hope this helped!
Good luck!

Raam

---

