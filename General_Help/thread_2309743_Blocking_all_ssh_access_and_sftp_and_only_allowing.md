---
title: "Blocking all ssh access and sftp and only allowing certain IPs to connect?"
date: 2016-01-13
forum: General Help
---

### Post by jakr2 on 2016-01-13
A lot of people from israel and china keep trying to log into my server via SSH I've looked online and I've only found tutorials to block people form visiting your site.
 I know how to block certain IP's and im monitoring the logs to see if there's any more attempts but I'd rather I set it so certain IP's can connect.

---

### Post by TheFu on 2016-01-13
Install fail2ban.

Wouldn't hurt to read this: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

---

### Post by SeijiSensei on 2016-01-13
Add these rules to your iptables ruleset:
```

/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.1 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.2 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.3 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -j REJECT

```
This will allow three clients to connect to the server and reject anyone else.

---

### Post by jakr2 on 2016-01-13
> **TheFu said:**
> Install fail2ban.

Wouldn't hurt to read this: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

> **SeijiSensei said:**
> Add these rules to your iptables ruleset:
```

/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.1 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.2 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -s ip.of.client.3 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 22 -j REJECT

```
This will allow three clients to connect to the server and reject anyone else.

Thank you.

---

### Post by TheFu on 2016-01-13
Those ip.of.client.1-3 can be subnets too.
I tend to think in terms of subnets, not individual IPs for firewall rules.

---

### Post by jakr2 on 2016-01-13
I know this is stupid but here goes, I keep getting ssh login attempts from china, Israel and now the Caribbean, of course I block there IPs but they keep coming it only started yesterday. One IP that I looked up seems to be coming from underwater in china is it possible that IP look ups are just getting confused or what? I've tried a few different look ups and there all coming back the same, I'm just curious as this is a bit strange.

---

### Post by howefield on 2016-01-13
Threads merged.

---

### Post by TheFu on 2016-01-13
> **jakr2 said:**
> I know this is stupid but here goes, I keep getting ssh login attempts from china, Israel and now the Caribbean, of course I block there IPs but they keep coming it only started yesterday. One IP that I looked up seems to be coming from underwater in china is it possible that IP look ups are just getting confused or what? I've tried a few different look ups and there all coming back the same, I'm just curious as this is a bit strange.

There is no practical way to block attempts like this from getting to your network edge. You can try to complain to the network owner in China, but don't expect anything to happen.  If you read my link above, you saw that you can move the ssh port to a non-standard port and that will make this even less interesting for the crackers around the world to bother with.  Better would be to have the edge router do the blocking and don't let requests even get to the server.  I have the routers do port translation, so from inside the network, ssh is on the default port and fail2ban works.  From outside the network, some high port must be used and the router forwards those requests to the specific server inside.  On 1 box, I don't block any connections, since people could be coming from almost any country in the world. We don't allow passwords for ssh authentication and after 3 failed attempts, that source IP is blocked for a day. That is usually enough to make them bored.

I see between 500 and 20K ssh attempts against my systems daily. After awhile, it is just background noise that gets logged and ignored.  When I don't see it, I look for issues with that specific server and ssh access. ;)  Usually there was an outage at the provider.

Be certain to use the ~/.ssh/config file to handle the non-standard ports for ssh too.  Every command I know that supports ssh connections honors those settings - rsync, rdiff-backup, scp, sftp all look in the config file for userid/port (and the other supported settings).  Plus the config file is a nice way to document my  different accounts userids/ports for different remote servers around the world.

---

### Post by jakr2 on 2016-01-13
> **TheFu said:**
> There is no practical way to block attempts like this from getting to your network edge. You can try to complain to the network owner in China, but don't expect anything to happen.  If you read my link above, you saw that you can move the ssh port to a non-standard port and that will make this even less interesting for the crackers around the world to bother with.  Better would be to have the edge router do the blocking and don't let requests even get to the server.  I have the routers do port translation, so from inside the network, ssh is on the default port and fail2ban works.  From outside the network, some high port must be used and the router forwards those requests to the specific server inside.  On 1 box, I don't block any connections, since people could be coming from almost any country in the world. We don't allow passwords for ssh authentication and after 3 failed attempts, that source IP is blocked for a day. That is usually enough to make them bored.

I see between 500 and 20K ssh attempts against my systems daily. After awhile, it is just background noise that gets logged and ignored.  When I don't see it, I look for issues with that specific server and ssh access. ;)  Usually there was an outage at the provider.

Be certain to use the ~/.ssh/config file to handle the non-standard ports for ssh too.  Every command I know that supports ssh connections honors those settings - rsync, rdiff-backup, scp, sftp all look in the config file for userid/port (and the other supported settings).  Plus the config file is a nice way to document my  different accounts userids/ports for different remote servers around the world.

Thank you for the response, that's a good idea I'll change the ssh port now.

---

### Post by TheFu on 2016-01-13
Please mark this thread as **SOLVED**, so others can see that and use the info too.

---

