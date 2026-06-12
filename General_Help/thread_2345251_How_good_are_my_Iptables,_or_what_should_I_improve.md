---
title: "How good are my Iptables, or what should I improve?"
date: 2016-12-02
forum: General Help
---

### Post by sebastiaan5 on 2016-12-02
Hello
I made some rules and add some from other sites but I still ain't 100% convinced that they are very strong and reliable. If anyone would be so kind to give me feedback about them I would appreciate that a lot.
I'm going to use them on my home server (but I want them to be very strong).
I use port 5000 to experiment with reverse proxied python apps.

```
*filter:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
:TCP - [0:0]
:UDP - [0:0]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -d 127.0.0.0/8 -j REJECT 
-A INPUT -m conntrack --ctstate INVALID -j DROP
-A INPUT -p icmp -m icmp --icmp-type 8 -m conntrack --ctstate NEW -j ACCEPT
-A INPUT -p udp -m conntrack --ctstate NEW -j UDP
-A INPUT -p tcp --tcp-flags FIN,SYN,RST,ACK SYN -m conntrack --ctstate NEW -j TCP


#  Allow HTTP and HTTPS connections.
# Port 5000 is for reverse proxied python apps
-A INPUT -p tcp --dport 80 -j ACCEPT
-A INPUT -p tcp --dport 443 -j ACCEPT
-A INPUT -p tcp --dport 5000 -j ACCEPT


# Accept ICMP
iptables -A INPUT -p icmp -j ACCEPT


#Block mysql other then 192.168.0.0
-A INPUT -p tcp -s 192.168.0.0/24 --dport 3306 -m state --state NEW,ESTABLISHED -j ACCEPT


# Allow SSH connections
#  The -dport number should be the same port number you set in sshd_config
-A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT


#Block DDoS
#maximum 25 connection per minute
-A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT 
-A INPUT -p tcp --dport 443 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT


# Log iptables denied calls
-A INPUT -m limit --limit 5/min -j LOG --log-prefix "iptables denied: " --log-level 7


#Block Syn-flood packets
-A INPUT -p tcp ! --syn -m state --state NEW -j DROP


# Syn scans blocking
-I TCP -p tcp -m recent --update --seconds 60 --name TCP-PORTSCAN -j REJECT --reject-with tcp-reset
#-D INPUT -p tcp -j REJECT --reject-with tcp-reset
-A INPUT -p tcp -m recent --set --name TCP-PORTSCAN -j REJECT --reject-with tcp-reset


-I UDP -p udp -m recent --update --seconds 60 --name UDP-PORTSCAN -j REJECT --reject-with icmp-port-unreachable
#-D INPUT -p udp -j REJECT --reject-with icmp-port-unreachable
-A INPUT -p udp -m recent --set --name UDP-PORTSCAN -j REJECT --reject-with icmp-port-unreachable


#-D INPUT -j REJECT --reject-with icmp-proto-unreachable
-A INPUT -j REJECT --reject-with icmp-proto-unreachable


# Drop everything else
-A INPUT -j REJECT
-A FORWARD -j REJECT


COMMIT
```

ps.
I've read about port knocking to, I think this is quite a good security measure but not many people use it why is that?

---

### Post by alexjpowell on 2016-12-02
Hi
More information is required

What is the machine being used for? Where does it sit in the overall network (eg home network behind a router, datacentre etc)

---

### Post by sebastiaan5 on 2016-12-02
Good question,

So the machine is being used mostly as web server, secondary as ssh tunnelling, owncloud, python reverse proxied applications, small database server.
My machine is sitting directly after my router so all traffic that comes troughs port 443, 80, 22 goes directly to this machine.

Greetings

---

### Post by Doug S on 2016-12-08
For your DDOS section:```
#Block DDoS
#maximum 25 connection per minute
-A INPUT -p tcp --dport 80 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT 
-A INPUT -p tcp --dport 443 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT
```I know that very many people do that. However, my experience has been that it doesn't work, and actually makes things worse. Why? Because while the system is under a DDOS, whenever the limiter decides it is O.K. for there to be a connection one of the bad guys snaps it up quickly, and the limiter kicks in again. So whenever a good guy comes along they are denied access.

EDIT: In your case it will never limit anyhow, because it is preceded by another ACCEPT rule, and thus will never hit this area.

For your SSH access:```
# Allow SSH connections
#  The -dport number should be the same port number you set in sshd_config
-A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT
```I would suggest, and have done so many times on these forums, that you implement an automatic bad guy detector. Example:```
# Dynamic Badguy List. Detect and DROP Bad IPs that do password attacks on SSH.
# Once they are on the BADGUY list then DROP all packets from them.
# Sometimes make the lock time very long. Typically to try to get rid of coordinated attacks from China.
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j LOG --log-prefix "SSH BAD:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -m recent --update --hitcount 3 --seconds 90000 --name BADGUY_SSH -j DROP
$IPTABLES -A INPUT -i $EXTIF -p tcp -m tcp --dport 22 -m recent --set --name BADGUY_SSH -j ACCEPT

```Note that I also make the following entry in /etc/ssh/sshd_config:```
#Limit the number of bad passwords per connection to 2. Default is 6.
#Then the iptables connection counter will kick in sooner to drop
#password attack hackers.
MaxAuthTries 2

```Hope this helps.

---

