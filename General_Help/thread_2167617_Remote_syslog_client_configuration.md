---
title: "Remote syslog client configuration"
date: 2013-08-14
forum: General Help
---

### Post by chakri78 on 2013-08-14
is there a way to force remote syslog to use different IP address.  I have a host with two same subnet IPs,  eth0:0 is floating IP address. I want the remote syslog to use floating IP address when it forwards the messages to remote syslog server. 

eth0 : 192.168.2.20
eth0:0 192.168.2.21

Could you please let me know how to achieve this? 

Thanks,

---

### Post by tgalati4 on 2013-08-14
I don't understand your question.  If you mean can I have rsyslog send syslog messages to 192.168.2.21, yes, make the change to /etc/rsyslog.conf.  If you need to send a marker message then use* logger --server 192.168.2.21 This is a remote marker message*.  But if the IP's change, then you will have to write a fancy script to capture the IP address and plug it into either rsyslog.conf or a logger script and then restart syslogd. 

Why can't you use a static IP for a server?  I would have at least one server (or VM) with a static IP and then have all other machines send remote syslog dumps as a backup.  There is no simple way that I know of to perform that function with changing IP's.  How often do the IP's change?  If it is on boot, then you can write a script to run on boot of the VM to capture the IP address and then modify rsyslog.conf and restart syslog--and hope it works as intended.

I don't understand the use case or what you are trying to achieve.

---

### Post by chakri78 on 2013-08-14
I have two hosts configured with  subnet IPs ( host1 192.168.2.19 and host2 192.168.2.20). using drbd with NFS, i configured an additional floating IP address 192.168.2.21 which floats betweens these hosts. Basically it is assigned to drbd primary host.  Both these hosts are configured to remote syslog messages to a third host. 

with default remote syslog configuration, both the hosts are able to remote syslog the messages to third host.  what i want is only the active host ( which has the floating IP assigned ) should do remote syslog. I thought one way of doing this is to use floating IP address as source IP for remote syslog. 

hope this clarifies...

Thanks,

---

### Post by tgalati4 on 2013-08-15
So you want a "dynamic" assignment of remote syslog such that only the active server sends syslog messages to a fixed IP server that is on 24/7 to capture such messages.

Other than the fancy script that I described, perhaps a fancy filter for syslog that accepts or rejects syslog messages based on which server is active.

I presume that your network is setup as follows?  

[http://www.howtoforge.com/high-availability-nfs-with-drbd-plus-heartbeat](http://www.howtoforge.com/high-availability-nfs-with-drbd-plus-heartbeat)

[https://help.ubuntu.com/community/HighlyAvailableNFS](https://help.ubuntu.com/community/HighlyAvailableNFS)

If this is the case, then remote syslog may not be the correct monitoring solution.  Perhaps Landscape, or GroundWorks, or some other enterprise monitoring would be called for.  Syslog (as a framework) is not designed for this use case or for High Availability clusters in general.  I'm not saying that you can't do it, it's just that there are better cluster management tools available than relying on a cobbled-together remote syslog script.

So, now I ask:  What specifically are you trying to monitor?  Uptime?  Disk health, Cluster health?, Directory availability?  I think there's a better way.  Remote syslog is helpful for a RAM-based NAS which goes down and takes its log files with the RAM.  That way you can go to a backup server and see what was going on before the NAS went down.  If the log files are kept on each host, and not in RAM (not VM's) then you want to monitor other things, because you will still have the log files to investigate if a host goes down.

I still don't understand the use case.

---

### Post by chakri78 on 2013-08-15
There is a fancy rule on the third host ( remote syslog server) which expects syslog messages from the floating IP address.  So all i want to do is when my active host forwards his syslogs to remote syslog server, instead of using his own IP, he should forward them using floating IP as source IP address. This might not be supported by remote syslog but can this be done using iptable rules? 

btw, all i'm doing is remote syslog, this includes syslog, auth.log and other logs files under /var/log/ on active host.

---

