---
title: "UFW firewall rules not effective against currently established connections."
date: 2022-06-22
forum: General Help
---

### Post by greenfreq on 2022-06-22
Situation:

I use UFW to block all traffic to a server running OpenVPN. (note that the server is running on an atypical protocol (TCP)
I create a rule to allow a specific address access to the OpenVPN server.
    example: sudo ufw allow from 1.2.3.4 proto tcp to any port 1234

When I am done with what ever I was doing with that client, I delete the firewall rule, and reload UFW.
    example: sudo ufw status numbered; sudo ufw delete #; sudo ufw reload

However, I am still able to see the client in "netstat" as established, and still able to ping the client via its VPN address.

I have tried stopping and starting the ufw service, but this does not work either.

This does not seem like it should be happening, as the encapsulated packets have to come in via the port that has been blocked. Even an explicit 'reject/deny' rule will not stop the traffic from continuing.  Is this some glitch with "Established Communications"?  Is there a way to get UFW to "flush" its established communications table?

---

### Post by Doug S on 2022-06-24
If you are finished with the connection, I am curious to know why it still shows as "ESTABLISHED" by netstat, as it seems the connection should have been terminated. Yes, UFW will typically allow RELATED,ESTABLISHED packets. UFW does not have flush control over the connection tracking table. UFW is just a front end for iptables, so you could enter a DROP rule before the RELATED,ESTABLISHED check (which I do not know to do via UFW).

---

### Post by #&amp;thj^% on 2022-06-24
> **greenfreq said:**
>  Is there a way to get UFW to "flush" its established communications table?

Fist show us this:
```
sudo ufw status numbered
```
EDIT: I'll add more here, When I make/change rules on the fly I'll usally use this:
```
sudo ufw disable

```
then I'll run:
```
sudo ufw reset
```
It should show you what's taking place, Example:
```
Output
Resetting all rules to installed defaults. This may disrupt existing ssh
connections. Proceed with operation (y|n)? y
Backing up 'user.rules' to '/etc/ufw/user.rules.20210729_170353'
Backing up 'before.rules' to '/etc/ufw/before.rules.20210729_170353'
Backing up 'after.rules' to '/etc/ufw/after.rules.20210729_170353'
Backing up 'user6.rules' to '/etc/ufw/user6.rules.20210729_170353'
Backing up 'before6.rules' to '/etc/ufw/before6.rules.20210729_170353'
Backing up 'after6.rules' to '/etc/ufw/after6.rules.20210729_170353'

```
This will disable UFW and delete any rules that were previously defined. This should give you a fresh start with UFW.** Keep in mind that the default policies won&#8217;t change to their original settings, if you modified them at any point.**

---

### Post by The Cog on 2022-06-24
As Doug S says, UFW allows ESTABLISHED connections to continue. This is perfectly normal practice. I can think of a few ways to stop that connection:
* Close the connection normally by closing the client app, whatever it is
* Edit the firewall iptables rules directly and block the specific connection you want to stop
* Restart the service it is connected to
* Use the firewall to block all connectivity until either the application or the Linux connection tracking times out.
* Install conntrack and use it to list all current connections, and delete the offending connection from the tracking list so it's no longer ESTABLISHED.
Actually, sudo conntrack -D --src <address> might be the easiest.

---

### Post by web-user on 2022-06-25
I had a similar issue with Docker. Turned out Docker works "outside" UFW because of its lower-level architecture, which bypasses firewall.

---

