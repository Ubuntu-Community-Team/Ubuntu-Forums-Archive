---
title: "How to configure ufw in 14.04 so as to drop unsolicited pings?"
date: 2014-10-05
forum: General Help
---

### Post by kpfuser on 2014-10-05
The above was a straightforward process for 12.04 . Following info in the wiki, one had to go to /etc/ufw/before.rules and edit the lines in the block "# ok icmp codes" so as to read

# ok icmp codes 
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP 
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP 
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP 
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP 
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

In the case of 14.04, I wasn't able to find specific info on how to carry out the same task. I attempted the same editing but got some (incomprehensible to me) error messages. Looking more closely, I saw that in the case of 14.04 the file /etc/ufw/bfore.rules is expanded to include a relevant-looking block of rules under the heading "# ok icmp code for FORWARD," i.e.,

# ok icmp codes for INPUT 
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP 
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP 
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP 
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP 
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP 

# ok icmp code for FORWARD 
-A ufw-before-forward -p icmp --icmp-type destination-unreachable -j ACCEPT 
-A ufw-before-forward -p icmp --icmp-type source-quench -j ACCEPT 
-A ufw-before-forward -p icmp --icmp-type time-exceeded -j ACCEPT 
-A ufw-before-forward -p icmp --icmp-type parameter-problem -j ACCEPT 
-A ufw-before-forward -p icmp --icmp-type echo-request -j ACCEPT

As the above shows, I edited the rules under "# ok icmp codes for INPUT" but left the rules under "# ok icmp code for FORWARD" as they were originally. My question is whether I did the right thing or I should have edited the "# ok icmp code for FORWARD" rules above to read DROP instead of ACCEPT. Can anyone shed some light?

---

### Post by Doug S on 2014-10-05
If your computer is not also a router and / or doesn't also have a virtual computer guest, then you should not have to worry about the FORWARD chain.
For pings, you only really need to worry about the "echo-request" lines.

Post your error messages here to help us understand better.

Disclaimer: I actually do not use ufw which is just a front end for iptables, but am good with iptables.

---

### Post by kpfuser on 2014-10-06
> **Doug S said:**
> If your computer is not also a router and / or doesn't also have a virtual computer guest, then you should not have to worry about the FORWARD chain.

My computer is a single laptop sitting behide a router. I have no idea what a virtual computer guest is and thus I guess I have no such thing in my system. Ergo I should not worry about the FORWARD chain. Am I right to assume that it is of no harm to set the rules in the FORWARD chain to DROP as well?
> For pings, you only really need to worry about the "echo-request" lines.
If memory serves me right, isn't possible that a would-be attacker can spoof pings of other types?
> Post your error messages here to help us understand better.
To do this I returned /etc/ufw/before.rules to its default state and edited it again using gedit. Upon closing gedit and opting for keeping the changes made, the following message appeared:

(gedit:2739): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:2739): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

Despite these error messages, editing the desired rules was successful.
> Disclaimer: I actually do not use ufw which is just a front end for iptables, but am good with iptables.
I have tried in the past to get started with iptables but I failed because I could not find any helpful study materials that would be simple enough for a begginer to follow. Could you suggest any? In any case, how did you get started in your ascend to iptable stardom?

---

### Post by Doug S on 2014-10-06
> **kpfuser said:**
> My computer is a single laptop sitting behide a router. I have no idea what a virtual computer guest is and thus I guess I have no such thing in my system. Ergo I should not worry about the FORWARD chain. Am I right to assume that it is of no harm to set the rules in the FORWARD chain to DROP as well?That would fine, yes. As would a policy of DROP for the whole chain. You will find that the FORWARD path is never traversed for your situation.> **kpfuser said:**
> If memory serves me right, isn't possible that a would-be attacker can spoof pings of other types?O.K. fair enough. but since your computer is already behind a router, you probably don't need to worry about it.> **kpfuser said:**
> To do this I returned /etc/ufw/before.rules to its default state and edited it again using gedit. Upon closing gedit and opting for keeping the changes made, the following message appeared:
(gedit:2739): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service filesOh, well that isn't related to ufw. I do not use gedit and don't know what is wrong here.> **kpfuser said:**
> I have tried in the past to get started with iptables but I failed because I could not find any helpful study materials that would be simple enough for a begginer to follow. Could you suggest any? In any case, how did you get started in your ascend to iptable stardom?Many of us find [this reference]("http://bodhizazen.net/Tutorials/iptables/") very good.
Ugh, I revise my earlier claim: I am mediocre with iptables. I have been studying iptables for several years. References I have used over the years (some now not so up to date) can be found at the bottom of [this]("http://www.smythies.com/~doug/network/iptables_notes/index.html").

---

### Post by kpfuser on 2014-10-07
Doug,

Thank you very much for your help. You have provided useful insights and a lot of material to sink my teeth in before I look for relevant help in the forum again. Thanks indeed!

---

