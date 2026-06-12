---
title: "ssh server on wireless /college network"
date: 2008-01-07
forum: General Help
---

### Post by cherry316316 on 2008-01-07
I use the wireless network provided to me by my college.
when I do
"ifconfig"
I get
eth1 inet addr:10.XXX.XXX.XXX
and
lo inet addr:XXX.XXX.XXX.XXX

now from remote, when I try
ssh <user_name>@10.XXX.XXX.XXX
its refuse to except my password.

also, from the other blog, i edited /etc/ssh/sshd_config file (file attached) and I added line
AllowUsers <user_name>

but its still not working. which IP address I am suppose to use.

i also followed the instruction on this website and did whatever written thr
[http://www.cyberciti.biz/faq/ubuntu-...configuration/](http://www.cyberciti.biz/faq/ubuntu-...configuration/)

but of no use so far. I have a firestarter (ubuntu firewall ) installed. i also opened the port 22 .I also tried with stopping it but no success.

then on one fine day, i put the lan wire in my laptop , the lan connection is also provided by college. i saw that my ip is now 131.X.X.X
and now when i tried from remote (basically all my college wired computers have ips in range 131.X.X.X) it worked.

so , the problem is for some reason, when i am on wireless , i have a different ip then the rest of wired computers in my college, and hence i am not able to connect to my laptop from ssh, but when i am on wired, it just works fine :((

---

### Post by heindsight on 2008-01-07
The wireless network that you're connecting to, is assigning you an IP address from a private IP
range (10.0.0.0 -- 10.255.255.255 are all private addresses). This means that while you're
connected to this wireless network, any service running on your computer is only accessible to
other machines on the same wireless network.

When you try to ssh to 10.x.x.x from a machine not on the same wireless network, you are
not actually connecting to your computer. Outside the 10.0.0.0 network, your 10.x.x.x address
has no meaning.

When you're connecting to the wired network, on the other hand, you're getting a public IP address,
and so anyone from anywhere on the internet (more or less) can connect to your computer using that IP address.

---

### Post by cherry316316 on 2008-01-07
> **heindsight said:**
> The wireless network that you're connecting to, is assigning you an IP address from a private IP
range (10.0.0.0 -- 10.255.255.255 are all private addresses). This means that while you're
connected to this wireless network, any service running on your computer is only accessible to
other machines on the same wireless network.

When you try to ssh to 10.x.x.x from a machine not on the same wireless network, you are
not actually connecting to your computer. Outside the 10.0.0.0 network, your 10.x.x.x address
has no meaning.

When you're connecting to the wired network, on the other hand, you're getting a public IP address,
and so anyone from anywhere on the internet (more or less) can connect to your computer using that IP address.


hi , thanks for the detailed reply. :)
can u tell me the solution for this problem.

just to let you know, i have BCAST and MASK number.
and also, when i check my ip address using some website,
which gives the ip, the website shows the ip which is in my college 
ip range (131.X.X.X).
now using any of this or is there any other way, i can connect to my 
laptop, while my laptop is on wireless.

thanks a ton in advance.

---

### Post by heindsight on 2008-01-07
I'm afraid there isn't really a solution.

When you connect to external sites, the wireless router uses IP masquerading to make it
appear as if your connection comes from its own public IP address. Return traffic from the
external site to you is then sent to the wireless router's public IP, the router then forwards this
traffic back to your laptop. So, the IP address you see when you look up your IP using an
external website, is actually the wireless router's public IP address. However, the wireless
router won't forward any new incoming connections to your laptop.

It is possible to configure such a router to forward incoming connections on its public interface
to machines on the internal (private) network. However, that only works if the machine on the
private network has a static IP address and you'd need root access to the router (and some
knowledge of how masquerading works) to set it up.

I'm afraid this is all a bit difficult to explain without getting into complicated technical details. If you're
interested you can do a bit of googling and read up on IP masquerading and Network Address 
Translation (NAT).

Just out of curiosity, where are you studying?

---

