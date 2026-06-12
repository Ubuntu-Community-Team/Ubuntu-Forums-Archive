---
title: "Strange firewall issue?"
date: 2007-10-09
forum: General Help
---

### Post by st0kes on 2007-10-09
Something odd has happened to my Ubuntu box that I installed yesterday.Not sure why but all of a sudden I can't browse it (apache) from another machine on the network, or ssh on to it, even though I know apache and ssh are both running ... I can open web pages when I am logged on to the actual box.I can ping it, but if I use nmap it tells me only ports 23 and 79 are open. When I try to ssh to it, it says 'connection refused' ... seems to be a firewal issue but I can't remember configuring any firewall on it! Is there anything that might have been installed with Gnome that would do this?

---

### Post by thirddeep on 2007-10-09
First, check if there is any firewall rules:
```
sudo iptables -L
```
Here is an example of NO firewall:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        
``` 

Thd.

---

### Post by Sef on 2007-10-09
> Is there anything that might have been installed with Gnome that would do this?

IPtables is installed by default.

---

### Post by st0kes on 2007-10-09
Mine looks exactly like yours. 

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

I can't get to the Internet from this machine either. This is really strange.

---

### Post by thirddeep on 2007-10-09
OK, lets get a couple of things straight.

Machine A is the one where you want to SSH onto. Machine B is the one you SSH from.

Is A and B on the same network ?

Can B ping A ?

Is there a firewall on B ?

Is there a firewall between A and B ?

Thd.

---

### Post by st0kes on 2007-10-09
Machine A = the one with the problem. IP 10.10.2.85

Machine B = Me. IP 10.11.12.70

Same network and same building, different vlans. But that should not be an issue as it was working perfectly yesterday. 

They can ping each other. But that's all they can do. There is no firewall on either machine.

---

### Post by thirddeep on 2007-10-09
OK.  Neither has firewall and there is no firewall between - just routing for the VLAN.

Ping is OK.

Are you in control of the router ?  Just because it worked yesterday does not mean someone did not change router configuration to block all but ping :-)

Next step, tcpdump.  I can not remember if tcpdump is installed by default.  If not, I'm sure you know how to install it :-)

On machine A (10.10.2.85) :
```
tcpdump -v port 22
```
That is assuming you have only one interface or/and that your using that interface for this network.  Else specify the interface.

Then from machine B (10.11.12.70):
```
telnet 10.10.2.85 22
```

See what output tcpdump gives.

Thd.

---

### Post by st0kes on 2007-10-09
Someone else manages the router but he assures me nothing has changed. Must be something to do with putting the gnome desktop on there as that's the only thing I've done. 

To be honest it will be faster for me to rebuild this box rather than troubleshoot the issue. Would be nice to get to the cause of this but I can't make time to do it. :)

Thanks for your help anyway.

---

