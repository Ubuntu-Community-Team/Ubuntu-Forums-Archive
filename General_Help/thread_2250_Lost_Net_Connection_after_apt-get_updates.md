---
title: "Lost Net Connection after apt-get updates"
date: 2004-10-26
forum: General Help
---

### Post by ions on 2004-10-26
[http://www.ubuntuforums.org/showthread.php?p=6971&posted=1#post6971](http://www.ubuntuforums.org/showthread.php?p=6971&posted=1#post6971) If you follow that link you'll see that I'm trying to admin a Ubuntu box via ssh.  

I used these commands:

```

apt-get update
apt-get dist-upgrade
apt-get upgrade

```

I don't know which one did it but no network functionality exists.  Pings fail.  Browsers do not connect.  

```
ping xxx.xxx.xxx.xxx (random IP)
connect: network is unreachable

```

ifconfig shows an IP and appears be in order.  

I ran dhclient and after a list of things it finished with this:

```
sudo dhclient
no DHCPOFFERS received 
no working leases in persistent database - sleeping

```

This is my neighbours box and they are on the same ISP as I am.  I am having no net problems.

So 2 things:

1.  How do I fix this?
2.  How can I update this box via ssh without borking it like this in the future?

---

### Post by ions on 2004-10-26
Cable connection.  No router.  :)

---

### Post by ions on 2004-10-26
Unplugging the cable modem and plugging it back in fixed this.

The 2nd problem still remains - how do I maintain this box via SSH so this does not happen again?

---

### Post by ions on 2004-10-27
[QUOTE=ions]Unplugging the cable modem and plugging it back in fixed this.

The 2nd problem still remains - how do I maintain this box via SSH so this does not happen again?[/QUOTE]
 It appears that unplugging the cable modem only temporarily fixed this problem.

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=ions]It appears that unplugging the cable modem only temporarily fixed this problem.[/QUOTE]

**Internet Connection**
Sounds like your ISP is having problems routing to that address.
Try sending a traceroute and printing what is displayed here.

**No Internet Connection**
If at the time when you go to ping, you may not have an internet connection present.  
```
sudo ifconfig eth0
```
This should display the IP address of your ISP Services (if availble)
If its not there, then your box isn't picking up the address provided by your ISP.  Also check and make sure that eth0 is running DHCP. 

On that note, please respond with a post of the situation afterwards.  Be sure to make sure none of the physical layer has malfunctions.  (cabling / hardware)

---

### Post by ions on 2004-10-27
[QUOTE=FLeiXiuS]**Internet Connection**
Sounds like your ISP is having problems routing to that address.
Try sending a traceroute and printing what is displayed here.

**No Internet Connection**
If at the time when you go to ping, you may not have an internet connection present.  
```
sudo ifconfig eth0
```
This should display the IP address of your ISP Services (if availble)
If its not there, then your box isn't picking up the address provided by your ISP.  Also check and make sure that eth0 is running DHCP. 

On that note, please respond with a post of the situation afterwards.  Be sure to make sure none of the physical layer has malfunctions.  (cabling / hardware)[/QUOTE]
 Annoyingly enough this was a cable modem problem.  The modem had decided to put itself in a sleep mode that even unplugging/replugging was not curing.  Thanks for the response FleiXius! :)

---

### Post by FLeiXiuS on 2004-10-27
[QUOTE=ions]Annoyingly enough this was a cable modem problem.  The modem had decided to put itself in a sleep mode that even unplugging/replugging was not curing.  Thanks for the response FleiXius! :)[/QUOTE]


Boo, I hate those sleepers!

---

