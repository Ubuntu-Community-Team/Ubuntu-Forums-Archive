---
title: "How to get VPN to work with Firestarter?"
date: 2005-10-16
forum: General Help
---

### Post by PeaceMessenger on 2005-10-16
I'm a noob, so please forgive me if something I say doesn't make sense.

I have been struggling to get my VPN working. I'm using PPTP-linux 1.5.0-5ubuntu and pptpconfig which I learned how to install from [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml) 

It works only if I disable the firewall in Firestarter.  I prefer not to do that because security is a priority where I am.   Firestarter has some things on it's website [http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php) about a workaround for a vpn. The work around they posted for connecting to a Microsoft VPN is :
> How to use the VPN workarounds in Firestarter 1.0

Copy the lines specific to your VPN solution listed below, and paste them into the /etc/firestarter/user-pre file on the firewall host. Restarting the firewall, for example by executing "/etc/firestarter/firewall.sh start", commits the new settings.
Microsoft VPN clients

The widely used VPN solution for Microsoft Windows machines is based on the PPTP protocol. The following lines allow PPTP clients on the Firestarter administered local network to connect to remote servers:

# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

OK, The first challenge I had was to open the /etc/firestarter/user-pre file for editing. I found it in the file directory, but it won't open. Aahh, I think I found why. It is owned by root. So I used the command under Applications-> System Tools->Run as different user and I typed gedit to open the text editor as root. Then I could open the user-pre file, which was absolutely empty. I cut and pasted the above lines into it, saved it, and then tried to restart the firewall. I couldn't figure out how to execute /etc/firestarter/firewall.sh start and so I decided to
just reboot the machine. That should restart the firewall, right?

Well, still no luck. I still have to turn off the firewall to make the vpn work. I decided to add a policy to firestarter. I added an inbound traffic policy to allow connections from the host, and entered in our VPN servers IP address. Hey, guess what... the vpn could connect- but still nothing works through it. It connects but then I can't even get to google. I turn off the firewall and everything works fine.

Any ideas what I am doing wrong? I think it must have something to do with how I am entering commands into the etc/firestarter/user-pre file. I would like to use the VPN and the Firewall both.  Please Help!  Thanks.

---

### Post by mirrro on 2005-10-22
Hey, I have the same problem ! ( in Hoary)
PeaceMessenger , look at the patch's note : "Forward PPTP VPN client traffic"

I think this patch is for Forwarding the pptp traffic  ... no?
(in a machine that act as a firewall..)

Some guys told me I need those kernel modules:
"ip_nat_pptp" and/or "ip_conntrack_pptp"

I didn't try those, yet... but I'm going too.

Hope to solve this too.:-?

---

### Post by reuben on 2005-11-28
Use GuardDog instead of Firestarter. Open VPN and PPTP in the internet zone.

---

### Post by jmooney on 2005-11-28
Well, this could be helpful for me anyways.  I've been trying to connect to my at work server via VPN and, though I can get an active connection, I can't do anything with it (like browse files).

As it turns out, I am running Firestarter and I had to set a policy to let the remote GNS (?) address through.

The website link is helpful, will try the fix tonight and, if I can get it to work, will post results here.

---

### Post by josteink on 2006-09-01
if you still have problems...

i came across this page looking for help with vpn (cisco) on my ubuntu 6.06 installation. i'using firestarter. to get vpn to work through firestarter i had to do the following:

1) as instructed on firestarter website ([http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php))
add the following work-around to /etc/firestarter/user-pre:

# Forward Cisco VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p udp --dport 500 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 500 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 50 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 50 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT 

2) restart firestarter (/etc/firestarter/firestarter.sh stop and then start)

3) allow inbound connection to my vpn-host in firestarter under policy

4) configure firestarter preferences/firewall/network settings such that internet connected network device is vpn0 (my vpn device) and local network connected device is eth0 (my network card). (you have to start firestarter after opening the vpn-connection for the vpn-device to show in your drop-down list).

=> 4) hasn't been mentioned above as far as i can see... so using firestarter works fine with my setup, no need to use guarddog...

j.

---

### Post by anuragj71 on 2007-01-20
Could you please elaborate on step 3 ?
I have opened ports 4500 and 500  required for the connection.
Step 4 - when I try to select interface cisipsec it complains that the interface is not ready.

I am trying this with cisco vpn client version 4.8.

---

### Post by Mulchman on 2008-02-07
I realize this is a REALLY old post but I found it while trying to get my Cisco VPN client to work with firestarter 1.03 & Ubuntu 7.10.

Through some google searching I found this site:
[http://www.lamnk.com/blog/vpn/using-firestarter-with-cisco-vpn-client/#comments](http://www.lamnk.com/blog/vpn/using-firestarter-with-cisco-vpn-client/#comments)

which said to put these entries in the user-pre file:
> iptables -A INPUT -j ACCEPT -s xxx.xxx.xxx.xxx -p esp
iptables -A INPUT -j ACCEPT -s xxx.xxx.xxx.xxx -p udp -m multiport &#8211;sports isakmp,10000
iptables -A INPUT -j ACCEPT -i cipsec0
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xxx.xxx -p esp
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xxx.xxx -p udp -m multiport &#8211;dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o cipsec0

and replace the xxx.xxx.xxx.xxx with whatever IP/host your VPN actually connects to. Also, the 2 "cipsec0" lines should be the name of your VPN device. In my case "cipsec0" was actually the name of my VPN device so a direct copy/paste (after changing the xxx.xxx.xxx.xxx lines) worked instantly for me. Of course, after changing the user-pre file you have to do something like:

> sudo /etc/init.d/firestarter restart

And, I did not need to set up any special rules/policies for anything either in firestarter.

---

