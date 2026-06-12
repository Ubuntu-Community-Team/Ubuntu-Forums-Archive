---
title: "How can I find the right port for Azureus?"
date: 2007-06-11
forum: General Help
---

### Post by CHB(tm) on 2007-06-11
Hey,
I installed Azureus and the download of torrents works so far - but the program told me that there must be a firewall or something that's blocking the used port, so I guess if I hit the right settings the downloads can be faster... when I try to test the "official" ports of Azureus, the test fails all the time after 20 seconds. :(
How can I find out what port is used, what port is supposed to be used and how I can open it?
I have the Dell Inspiron E1505 with Ubuntu :)
Thanks for your answers :)

---

### Post by CHB(tm) on 2007-06-11
After reading a lot of entries about my problem I found out that I have to forward the port(s) to my router... how?? My router is a Westell Versalink 327W!

---

### Post by dpar on 2007-06-11
Open Azureus, under Tools>Options>Connections it should list the port it is using. Sorry, I know nothing about that particular router.

---

### Post by CHB(tm) on 2007-06-11
It tells me it's using port 54576... but when I perform the port test under the Configuration Wizard the test fails.
I guess I have to log on my router and forward the port... but I don't know how.

---

### Post by CHB(tm) on 2007-06-12
And you guys don't know it either...?! :(

---

### Post by EricWiz on 2007-06-12
CHB,

I put this into google:
Westell Versalink 327W + azureus

This was first on the list:
[Port Forwarding for the Westell Versalink 327W]("http://portforward.com/english/routers/port_forwarding/Westell/Versalink-327W/Azureus.htm")

That should help. 

Eric

---

### Post by neorou on 2007-06-12
I vaguely remember helping my uncle with a Westell router last year.

It has it's own IP address. Open a web browser and enter the IP address. Usuallly the IP address of 192.168.1.1 (I am getting this info from this site [http://www.thinkbroadband.com/hardware/reviews/2004/q3/westell-proline-6000.html](http://www.thinkbroadband.com/hardware/reviews/2004/q3/westell-proline-6000.html)).

You will need an admin username and password. If you have trouble, contact your ISP, they'll tell you how to reset it.

When you get to the firewall configuration, the easiest thing to do would be to forward all IP traffic to your computer's internal IP address. This opens up your computer to attacks though, so be forewarned. 
By default these routers set a DHCP (dynamic addressing). Unless there are many computers and they turn on and off at different times, you will most likely get the same IP address from the router every time.

Go to Network Administration control panel, under System menu item, and select the appropriate connection (wired or wireless). Click on Properties and see what your IP address is. Use that address to forward all of your port requests.

A better option would be to select a port and specify that port in the port configuration panel of the Westell modem. Once you get into the controls it should be easier to figure out.

Good luck...

---

### Post by CHB(tm) on 2007-06-12
> **EricWiz said:**
> CHB,

I put this into google:
Westell Versalink 327W + azureus

This was first on the list:
[Port Forwarding for the Westell Versalink 327W]("http://portforward.com/english/routers/port_forwarding/Westell/Versalink-327W/Azureus.htm")

That should help. 

Eric
Thank you Eric, but I was on that homepage already and it's for Windows.

@neorou:
Thanks for your help so far... I made it into the configuration of the router. But I don't know which one of these options I have to choose:
[I]-  Forward a range of WAN ports to
   an IP address on the LAN
-  Forward a range of ports to an IP
   address on the LAN only after
   specific outbound traffic[/I]

Okay, I just went with the trigger port option (the second one) and enabled port 50000. How can I open that one in Ubuntu now? Azureus still says that the test fails when I try to test port 50000

---

### Post by CHB(tm) on 2007-06-12
Okay, I "opened" the port with
```
 sudo iptables -A INPUT -p tcp --dport 50000 -j ACCEPT

```
but Azureus still tells me

[I]Testing port 50000 ... 
NAT Error - Connect attempt to xx.xxx.xx.xxx:50000 (your computer) timed out after 20 seconds. This means your port is probably closed.[/I]

---

### Post by mills on 2007-06-12
the site ericwhiz linked to is pretty much os independent just ignore the blue window edges you associate with windows os and follow the instructions, i see no reason why that page wont apply in Linux. azureus is the same in both os's and so is your router page
enter your router address (gateway) into your browser's url bar and follow the instructions

your router has its own firewall so you either need to configure that  or do as i've done and switch it off or forward the port from your router page

[westell forums that might help further]("http://www.dslreports.com/forum/westell")

---

### Post by CHB(tm) on 2007-06-12
Alright, thanks guys! I'll dig in it and try to figure it out :)

---

### Post by EricWiz on 2007-06-15
Hey CHB..


How's it going? Any luck?

---

