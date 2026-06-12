---
title: "Mac OS Server"
date: 2018-01-26
forum: General Help
---

### Post by oliver172 on 2018-01-26
As Apple announced yesterday, they're basically getting out of the MacOS "server" market with a forthcoming 2018 update to 5.4 -- at least as far as I use a server (DNS, DHCP, etc.).

I've not used Ubuntu in a long time and never the server product so I'm wondering how difficult it is to set up DNS, port forwarding, Tomcat, etc., compared to the MacOS which automatically configures the AirPort Extreme router and such.

Just trying to get a read on Ubuntu Server as that will most likely be what I transition to.

Are there good tutorials or documentation to walk people through these setups? I'm assuming Ubuntu Server comes with everything I'd need.

Thanks in advance for any suggestions or information.

- O

---

### Post by TheFu on 2018-01-26
Welcome to the forums.

"Good" is highly subjective, so it would completely depend on your level of skill outside point-n-click tools.  There isn't any point-n-click on Linux servers.  Adding 3rd party web-apps to provide point-n-click is a security mistake, increases viable attack vectors and usually makes for a less-stable server.

If you want port-forwarding, then you want a Linux router.  That is different from DNS or a Java application server like Tomcat.  Please segment these services onto different devices/virtual machines.  
DNS has historically been very hackable.  Best practices have a master and a slave DNS setup, with the slave providing services to users.  The master is NOT on the internet and cannot be reached by anyone except the DNS admin team.  I've been hacked 2 times in my career.  Once via DNS.  I pay professionals to handle external DNS. $20/yr provides great peace of mind. They can be expert on DNSSEC, spoofing attacks, and reflection attacks. 
Java definitely shouldn't be on the DNS or router.

Much of the documentation for any Linux server is generically provided by the project team for that specific service.  There isn't just 1 DNS server. There are probably 10. Which you use will determine the documentation quality.  There are simple DNS servers and there are kitchen-sink ones that meet every possible rule for what a DNS should provide.

But you probably just want something like: [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) ... for people who want a consistent, how-to style, there must be 50 dead-tree books about ubuntu server. Those can be excellent, consistent, resources for people who just want to know what to type.  I don't know how secure the resulting services will be - security [y/n] isn't a checkbox, after all.
help.ubuntu.com has a wiki with guides for most server things too.  Most of the time, setting up a simple service is 5 commands, but that just gets it working. To secure it is another 20 steps.  Be careful with any service setup guide that doesn't include 20 steps for security too.  Even something as simple as ssh has 10 extra steps to get security going.

Ubuntu Server ties into the Debian and Canonical repositories.  From there, you can load over 45,000 packages, for free, with few strings.  The code for all of them is available. You are free to modify the code AND to re-release those modifications without fear of someone else suing.  So, in the strictest sense of your question, "everything you need", the answer is no, but you can install the extra packages to extend the OS as needed. Relearn about the package management methods.

IMHO.

---

### Post by oliver172 on 2018-01-27
Thanks very much for that great info.

I do basic Linux administrator but hardly an expert in installation.

I've bookmarked your link for future reference.

Thanks again.

---

### Post by TheFu on 2018-01-27
a) glad it is helpful.
b) Becoming a "power user" will make your life in Linux easier. Here's how, in the fastest, no hassle, no personal info required, way I know: [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) 
c) Please mark this thread as "solved" using thread tools button. That helps others seeking help and looking to help.

---

### Post by oliver172 on 2018-01-27
I marked it solved....thanks again! :)

---

