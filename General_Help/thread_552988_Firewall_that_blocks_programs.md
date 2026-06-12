---
title: "Firewall that blocks programs?"
date: 2007-09-17
forum: General Help
---

### Post by Kenobi on 2007-09-17
Hi,

everyone talks about firestarter but this program only blocks computers, not programs. But recently I found out that my computer starts communicating heavily to the internet once I leave the computer for more then 5 minutes. I want to know which program that is and want to block that. 

I want a message like: "do you want to allow [executable name] to connect to the internet?", whenever a new program tries to set up a connection.

Hope you can help me,

---

### Post by Steve1961 on 2007-09-17
> **Kenobi said:**
> Hi,

everyone talks about firestarter but this program only blocks computers, not programs. But recently I found out that my computer starts communicating heavily to the internet once I leave the computer for more then 5 minutes. I want to know which program that is and want to block that. 

I want a message like: "do you want to allow [executable name] to connect to the internet?", whenever a new program tries to set up a connection.

Hope you can help me,

I'm not aware of a Linux firewall that will give you that type of message, but you could try an alternative such as Guarddog which contains more configuration options.

---

### Post by expatCM on 2007-09-17
But are you really not asking simply what is running?  If you are to block something you need to find out what it is.  Not all processes are harmful ....  but yes it is a good idea to play safe.

Could either of the following commands help you out at all?

Show running processes
ps -A

Show open ports and what is using them
sudo netstat -tcp -p

---

### Post by Kenobi on 2007-09-17
No, thats not enough, but thanks for that tip, thats a good first step.

I want to be able to BLOCK programs if needed and I want an INSTANT notification when a new program tries to connect. Just think of troyans, you won't be able to stop them if you don't know they're running!

So is there anything for that job?

---

### Post by pxwpxw on 2007-09-17
**Kenobi**

I think I know what you mean.
A program that monitors outgoing network connections and programs, and lets you build a control list - yes like Little Snitch in Macosx and some of the windows firewalls.
You can see some of this info using netstat socket info
```

sudo netstat -aenptc
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     0          18307      4974/hpiod          
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     0          20756      5566/cupsd          
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     108        18318      4977/python         
tcp        0      0 10.1.1.20:60608         91.189.94.186:80        ESTABLISHED1000       23250      5480/firefox-bin    
tcp        0      1 10.1.1.20:60609         91.189.94.186:80        SYN_SENT   1000       23252      5480/firefox-bin    
tcp        0      0 10.1.1.20:33631         209.85.139.104:80       ESTABLISHED1000       22841      5480/firefox-bin    

```
This can also be monitored using the iptables firewall to detect new outgoing connections.
Just needs someone to write a program to do it. 

I would like one also, have not found anything so far.

---

### Post by Bd0g on 2007-10-25
This definetly got my vote. I've been using Outpost for a long time with WinXP and the application control is most wanted in Linux. Neighbour is using "Little Snitch" right now... and I really miss that kind of ability.

---

### Post by jshurst on 2007-10-25
I would like to see that, but at least you can use firestarter and set the outbound connections to "Restrictive by default" then just whitelist certain ports (like 80, 443, 21, etc).

---

### Post by Kenobi on 2007-10-26
Yeah, thats a minimum solution.... which does some good but the whole thing won't help you if the program you want to block uses a standard port :P We need a proper program!

---

### Post by mahousaru on 2007-10-26
*scratches head*
Hmmm the closet thing I think that is available is to use TCP Wrappers which also allows you to allow/deny services listed in inetd/xinetd.  Since the files there point to actual binaries that will give you a more granular control.  The problem is this is for incoming only.  

I guess the main issue with nix users is we haven't had years of MS phone home c**p shoved down our throats to inflict a deep rooted paranoia :(

If it is warning of outgoing you want, then you could setup the outgoing tables to be deny all, set a rule to allow for connection tracking, allow ports u know you want (ie port 80, 443 etc) and then set up a final rule to log and drop all.  Then set up psad to email you as soon as soon as you get a serveral packets being rejected, that way u can then add a rule for a wanted app, or investigate why a unwanted up is trying to connect out.

seems like a lot of work to me...  

but to get u started a iptabes script just for outgoing would look like below..  The important part is the log and drop bit at the bottom, that way psad can pick up the logs and then warn you via an email, or if u wish, use an external script to pipe the message to your console.

```

IPTABLES=/sbin/iptables

# Set policies on default chains
$IPTABLES -P INPUT DROP
$IPTABLES -P FORWARD DROP
$IPTABLES -P OUTPUT DROP

:
cropped
:

# *** OUTPUT policy ***

# Allowed approved connections 
# (Note: the I and 1 ensures that this is the first rule in the OUTPUT chain at this point in time)
$IPTABLES -I OUTPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow outbound ping (I like to ping if you don't like to ping then rem this out)
$IPTABLES -A OUTPUT -p icmp -j ACCEPT --icmp-type echo-request

#DNS
$IPTABLES -A OUTPUT -p tcp -d 192.168.0.1 --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp -d 192.168.0.1 --dport 53 -m state --state NEW -j ACCEPT

# Allow FTP Client
$IPTABLES -A OUTPUT -p tcp --dport 21 -m state --state NEW -j ACCEPT

# Allow SSH Client
$IPTABLES -A OUTPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT

# Allow HTTP Client
$IPTABLES -A OUTPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT

# Allow HTTPS Client
$IPTABLES -A OUTPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT

# Log and drop everything not accepted above
$IPTABLES -A OUTPUT -j LOG --log-prefix "Dropped by OUTPUT "
$IPTABLES -A OUTPUT -j DROP

```

---

### Post by thirddeep on 2007-10-26
Actually, the answer is simple : SELinux

The implementation might not be simple, but the answer sure is :-)

Tuning your firewall to only allow outgoing on port X, does not work.  As any application could then go out on that port.

Thd.

---

### Post by mahousaru on 2007-10-26
> **thirddeep said:**
> Actually, the answer is simple : SELinux

The implementation might not be simple, but the answer sure is :-)

Tuning your firewall to only allow outgoing on port X, does not work.  As any application could then go out on that port.

Thd.

SELinux requires a 10th level black belt grandmaster uber ninja geek to configure properly.  AppArmor is much easier....

---

### Post by pxwpxw on 2007-10-27
> **mahousaru said:**
> SELinux requires a 10th level black belt grandmaster uber ninja geek to configure properly.  AppArmor is much easier....
 
And AppArmor is installed in Gutsy  by default.

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

$ dpkg -l apparmor
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                  Version               Description
+++-=====================-=====================-==========================================================
ii  apparmor              2.1+993-0ubuntu3      User-space parser utility for AppArmor
$ 

Now to find out how it works, and why there was no sign of its presence, configuration, or activation.
Nice to find these things out eventually..

---

