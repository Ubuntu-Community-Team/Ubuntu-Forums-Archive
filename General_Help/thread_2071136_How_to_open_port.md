---
title: "How to open port"
date: 2012-10-14
forum: General Help
---

### Post by fizikz on 2012-10-14
How can I which ports are open/closed on my system? I am running Ubuntu 12.04, and to my knowledge there is no firewall running or installed, although it may have been in the past. 

I am trying to configure Deluge because currently no incoming connections are being allowed. I checked that UPnP is enabled on the router and also configured port forwarding. I tried running Deluge with UPnP and random ports, and also with specific port ranges according to the forwarded ports on the router. Neither worked. On [http://canyouseeme.org/]("http://canyouseeme.org/") the ports I try are always giving "Connection time out," even for the port I have configured for SSH. I have verified that I can SSH without any problems.

Any advice on how to get Deluge to accept connections and to understand the situation would be appreciated.

EDIT: I can SSH into my computer via another computer on the home network, but it seems it cannot be reached from the outside.

---

### Post by papibe on 2012-10-14
Hi fizikz.

I would first try to determine if you are being block at the router level or at the machine itself. 

Do you have other machine to test LAN ssh access?

Regards.

---

### Post by fizikz on 2012-10-14
I do have other machines with which to test. I have just tested that it is able to SSH to my main machine. However, testing from outside the network seems to fail. According to [http://canyouseeme.org/](http://canyouseeme.org/) any port I tried, including 80, my SSH port, Deluge ports, etc all return "Connection time out."

I think that my router is configured correctly (port is forwarded), but I would not mind some extra tests.

---

### Post by papibe on 2012-10-14
Is your machine set with an DHCP reservation or an static LAN IP?

Could you post an screenshot of your router's forwarding rules?

Regards.

---

### Post by fizikz on 2012-10-14
I have a static IP on the home network, and I have verfied that I am getting the IP (in connection information) that I reserved for this machine. 

I have attached a screenshot of the router's port forwarding page. The router is an Engenius ESR-9850.

---

### Post by papibe on 2012-10-14
Forwarding looks OK (make sure there's contradicting rules on the range's page).

Sometimes ISPs block standard ports like 22 (ssh), 25 and 80.

Without changing your port locally (your Ubuntu machine), you can forward a higher port to your local 22 in order to test this theory.

For instance, you can try a port in the dynamic range: 49152&#8211;65535

Let us know how it goes.
Regards.

---

### Post by fizikz on 2012-10-14
I don't think my ISP blocks ports. Also, I have set up a different port (both public and private) for SSH (and Deluge) than the default. So, I am not using 22 for SSH. For Deluge I have a port in the dynamic range in the router's forwarding page. It is still not working. Since it doesn't seem like the router is at fault, how would I go about checking to see if the system's port handling settings are in order?

---

### Post by papibe on 2012-10-14
Besides canyouseeme, have you tried connecting from outside? (connecting from inside your network to your public IP, or public domain name usually won't work).

Try using [Nmap Online]("http://nmap-online.com/"). Post your results if you would.

Regards.

---

### Post by fizikz on 2012-10-14
On attempts to scan normally with Nmap I get the error: "Note: Host seems down. If it is really up, but blocking our ping probes, try -PN"

With the option -PN enabled, the results were: "All 5000 scanned ports on ***IP*** are filtered" What does that mean?

---

### Post by papibe on 2012-10-14
Are you sure you are scanning your own public IP?

Regards.

---

### Post by fizikz on 2012-10-14
Yes, I compared the IP scanned with [www.whatismyip.com](www.whatismyip.com) and they match.

---

### Post by papibe on 2012-10-14
Have you upgraded the firmware recently?

It looks like your router has some problems with port forwarding. Apparently, they can be fixed upgrading the firmware (read [here]("http://engeniusforum.com/viewtopic.php?f=21&t=106")).

Let us know how it goes.
Regards.

---

### Post by fizikz on 2012-10-14
Wow thanks for pointing that out. That is really odd for a router to fail at a standard router function such as port forwarding. In any case I do have the latest firmware v2.1.3. I'll have to search more about port forwarding issues with this router.

I also tried the open port checker with the router's firewall disabled, and then also by bypassing the router altogether and plugging in directly to the modem. It still didn't see my ports which should be open for SSH and Deluge.

---

### Post by fizikz on 2012-10-15
Success! The problem was that I had to create rules on the modem (Thomson ST516) under "Game & Application Sharing" to assign traffic on a port (or range of ports) to a given device, in this case, my router. With port forwarding set up on the router, and the applications (Deluge, SSH) set up on my computer, everything now works as it should. 

I had not thought of the modem before since I have the firewall on it disabled. The clue for me was when I did some zenmap scans and saw only 5 ports open (80, 443, 1723, 21, 23) and the name of my modem showing up many times, sometimes referred to as a router.

This has been bugging me for a long time, so I'm very happy it's solved. Thank you, papibe, for your help!

---

### Post by papibe on 2012-10-15
Ohh! double NAT?!

:) I'm glad your sorted out.

Regards.

---

