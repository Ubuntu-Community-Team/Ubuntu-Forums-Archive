---
title: "Need help with understanding Ubuntu about setting up users, DHCP, firewalls and so on"
date: 2015-10-05
forum: General Help
---

### Post by Ashell_Seasucker on 2015-10-05
Well i got a task at school where me and the group i am in was supposed to set up Ubuntu with DHCP, set up a firewall, set up users, make users be able to connect to a printer and connect to a free VPN service. 

The first problem with this task is that me and the group are completly new to Ubuntu, and i am on a group with people that would rather sleep instead of searching up information on Ubuntu and how to use it. 
Our teacher said we were not supposed to get help from him, we should rather search up on the internet how to do the things we need to do.

Just so you guys know also the task is over and me and my group failed at it, so right now i am in my autumn vacation and want to use that time to get better at it.

So the thing i am asking is if someone is willing to help me and teach me how i should go trough with this and put it up, the help is really appreciated since i want to get better at this.

The task text (Translated from Norwegian):

What the business needs:


The business needs help with Linux andprogrammable switches,
the switches are of the types CiscoCatalyst and HP ProCurve.


A unit that doesnt to many resourcesand is stable (Went for Ubuntu here)


A firewall.


A free and stable VPN solution.


A DHCP-server that gives users comingtrough the VPN an IP address in the internal network.


When the user is logd in they should beabel to user the printer that's in the office.

The Ubuntu version used is Ubuntu Desktop 14.04.3 LTS

---

### Post by Lars Noodén on 2015-10-05
> **Ashell_Seasucker said:**
> Well i got a task at school where me and the group i am in was supposed to set up Ubuntu with DHCP, set up a firewall, set up users, make users be able to connect to a printer and connect to a free VPN service. 

We can't do the homework for you, I can't find the link about it, but there is some kind of policy here at the Forums.  That said, you can get pointed in the right direction when you get stuck.  

Ubuntu 14.04, as you have chosen, is a good choice because it has support through 2019 and won't be changing except for security updates.    But are you looking to set up a desktop system or a server for a small business?

---

### Post by Ashell_Seasucker on 2015-10-05
I dont think its supposed to be a server for a small business, since it's only needed that a user can log on trough the VPN service and use the printer.

Also i am mostly just looking for a point in the right direction for what i should do, so i learn something from this istead if falling behind because of a failed task.

---

### Post by Lars Noodén on 2015-10-05
Well, for a desktop, the firewall interface is UFW which is a front end to iptables.  The UFW interface for iptables is rather simple and if you look in the repository you can even find and add a graphical interface for it.  

For the VPN, which have you looked at?  If you are looking to provide your own VPN service, OpenVPN is popular.  If you are looking to use an existing VPN service, then there is also a section on VPNs in the official desktop guide.  You can browse the guide more generally for points relevant to your tasks, such as the section on networking:

[https://help.ubuntu.com/14.04/ubuntu-help/index.html.en](https://help.ubuntu.com/14.04/ubuntu-help/index.html.en)

I think that printing is in there too, but printing and I haven't gotten along since 94 or so.

---

### Post by Ashell_Seasucker on 2015-10-05
Thanks for the help, is it ok if i ask more questions later if i get stuck?

---

### Post by Lars Noodén on 2015-10-05
No problem.   There are people around 24/7 due to the international nature of the Forums so feel free to ask when you need to.

---

