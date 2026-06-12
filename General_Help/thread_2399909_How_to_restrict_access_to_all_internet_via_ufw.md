---
title: "How to restrict access to all internet via ufw?"
date: 2018-08-31
forum: General Help
---

### Post by webmiester on 2018-08-31
Hi everyone,

I am making a kiosk system for a company system.  Preventing people from using the kiosk to browse the internet has been crazy...  I want to restrict the computer to allow entry only to one site.  Let's say it is 192.123.12.123, and if they put anything else, it would fail.  What command lines in the terminal should I put?  If it works, ill put it in as a bash script to be loaded everytime the terminals startup.

Before this, I tried putting in the whitelist and blacklist in the GUI firewall of ubuntu 16.04 but it didnt do anything.  Once I load a browser, the browser can go anywhere :(

I want to try it again though, and ask for your advice, re command-line restrictions.  I believe this should be done by IPtables.  When I read the documentation of the IPtables, I get really confused, so if its ok, I would just like to ask for advice. Thanks so much.

---

### Post by SeijiSensei on 2018-08-31
```

/sbin iptables -A OUTPUT -d 192.123.12.123 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```

First line allows traffic out to the designated address. Second line blocks all other outbound traffic.

I don't use UFW. I just write the rules myself. Usually I invoke them from /etc/rc.local.

---

### Post by webmiester on 2018-09-01
SeijiSensei,

Thank you so much.  You have been very helpful even with my other posts.  Ill look up the "/etc/rc.local" that you use

With the script you gave:

/sbin iptables -A OUTPUT -d 192.123.12.123 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

If I make it "INPUT" instead of "OUTPUT" such as

/sbin iptables -A INPUT -d 192.123.12.123 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

Will this prevent other computers from accessing my machine?  So, like if I put this into my ubuntu server, will it be able to prevent unauthorized people from accessing it?

Lastly, if what I need to put is a range of IPs or several IPs, what would be the syntax?  Can I just use the following lines:

/sbin iptables -A INPUT -d 192.123.12.123 -j ACCEPT
/sbin iptables -A INPUT -d 192.123.12.124 -j ACCEPT
/sbin iptables -A INPUT -d 192.123.12.125 -j ACCEPT
/sbin iptables -A INPUT -d 192.123.12.126 -j ACCEPT

/sbin iptables -A INPUT -d 192.123.12.140 -j ACCEPT
/sbin iptables -A INPUT -d 192.123.12.142 -j ACCEPT
/sbin/iptables -A INPUT -j REJECT

Or is there an easier way to write this?

Thank you so much.

---

### Post by SeijiSensei on 2018-09-02
Well you can use subnet addressing like 192.123.12.0/24, but that will permit 192.123.12.1-254.

> Will this prevent other computers from accessing my machine?

Yes, or you can use a "policy." Make sure you permit port 22 if you communicate with this machine over the Internet.

iptables is complex with many options. See [https://linux.die.net/man/8/iptables](https://linux.die.net/man/8/iptables)

---

### Post by webmiester on 2018-09-03
Thank you so much.

---

### Post by webmiester on 2018-09-03
I placed it at the /etc/rc.local file and it worked so well!

Now lets say I want the computer to have access to our server which I theoretically is 192.168.0.100, and then I also want that same computer to be able to access gmail but nothing else.

Will these lines work to do what I would like it to do?


/sbin iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT
iptables -A INPUT -p tcp --dport 80 -m account --aname [http://www.gmail.com](http://www.gmail.com) --aaddr 192.168.0.0/24 --ashort
iptables -A OUTPUT -p tcp --sport 80 -m account --aname [http://www.gmail.com](http://www.gmail.com) --aaddr 192.168.0.0/24 --ashort

So in this case, gmail.com should work but everything else except for those in 192.168.0.0-255 should have access right?
Is this correct?

Then let's say I want my server to be accessed by only those with IP addresses 192.123.12.0 up to 192.123.12.100

Will this syntax be correct?
/sbin/iptables -A INPUT -d --src-range 192.123.12.0 - 192.123.12.100  -ip -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

Is this right?  You see, it I type in something wrong, I think these lines are rather hard to test.  I need to use a computer with an IP outside this range just to test if this works, so I would like to know if my syntax is correct

---

### Post by webmiester on 2018-09-04
[QUOTE=SeijiSensei;13797360]Well you can use subnet addressing like 192.123.12.0/24, but that will permit 192.123.12.1-254.


I think I got it working!  Thanks so much.  I was able to put ipTables in my server so that only a specific computer can ssh into it, and only a specific range can access it.  I hope it works perfectly.

Thanks so much!

---

### Post by webmiester on 2018-09-04
Hi SeijiSensei,

I want to thank you for helping me out.  I was able to get the IPtables to work as I would like on computer kiosks I was working on.  My next problem was the server.  What I would like is that only computers with an IP address of 192.123.123.0 up to 192.123.123.99 can communicate with the server, while those with any other address will be dropped or rejected, specially those with an IP of 192.123.123.100 up to 255 since these are the addresses to be given by the DHCP server to our guests.

So here is what I've done in the rc.local file of the main server:

# Allow access from known computers
/sbin/iptables -A INPUT -i eno1 -m iprange --src-range 192.123.123.0-192.123.123.99 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.10.0/24 -j ACCEPT

# Drop all other connections
/sbin/iptables -A INPUT -i eno1 -m iprange --src-range 192.168.10.100-192.168.10.255 -j DROP
/sbin/iptables -A OUTPUT -j DROP
/sbin/iptables -A input -j DROP

# Activate Firewall
ufw enable
exit 0
 

Now I tested it by logging on to our system through my phone on with an IP of 192.123.123.200 and it still was able to access the server.  I dont get it :(

---

### Post by sporksrule on 2018-09-04
> **webmiester said:**
> Hi everyone,

I am making a kiosk system for a company system.  Preventing people from using the kiosk to browse the internet has been crazy...  I want to restrict the computer to allow entry only to one site.  Let's say it is 192.123.12.123, and if they put anything else, it would fail.  What command lines in the terminal should I put?  If it works, ill put it in as a bash script to be loaded everytime the terminals startup.

Before this, I tried putting in the whitelist and blacklist in the GUI firewall of ubuntu 16.04 but it didnt do anything.  Once I load a browser, the browser can go anywhere :(

I want to try it again though, and ask for your advice, re command-line restrictions.  I believe this should be done by IPtables.  When I read the documentation of the IPtables, I get really confused, so if its ok, I would just like to ask for advice. Thanks so much.

UFW rules are applied in a certain order, so if you deny all incoming then subsequently allow a specific IP address, the first rule is honored.

Theefore, do something like this:

Use this command to see the numbered rules:
```
sudo ufw status numbered
```
Then delete rule in the wrong position:
```
sudo ufw delete 4
```
Then add the rule back to the number 1 position:
```
sudo ufw insert 1 allow from [ip-to-allow] to any
```

---

### Post by webmiester on 2018-09-06
I discovered that if I put "ufw enable", then the iptables that I configured don't work.  I think I might need to configure the iptables through the firewall and not via startup command line.

---

