---
title: "setting up azureus need help port forwarding"
date: 2007-06-19
forum: General Help
---

### Post by Atrio05 on 2007-06-19
I am trying to set up azureus correctly to download torrents i need help with the port forwarding part. Im not able to open any ports correctly due to my dsl modem (speed stream 4200) and my router (buffalo .. not sure) ive tryed numerious ways to open the ports but all have failed except for unplugging the router and useing the dsl modem by itself i really need to have the router because i have mutiple computers, i really appreciate it if anyone can help me forward ports with both router and modem. 

can somebody help me out?

---

### Post by cogadh on 2007-06-19
[http://www.portforward.com/](http://www.portforward.com/)

Has specific instructions on nearly every type of router out there.

---

### Post by Atrio05 on 2007-06-19
the only help on there is for windows only.

---

### Post by kelvin spratt on 2007-06-19
Its the router you set up its the same for linux

---

### Post by kelvin spratt on 2007-06-19
put the name of your router the put in the blue frog, it will give you step by step instuctions on how to setup your router You don't touch Linux And its its the same setting in both so if you have the frog setup in windows you use the same ports in the frog,in Linux and vice verser your distro does not need altering

---

### Post by cogadh on 2007-06-19
> **Atrio05 said:**
> the only help on there is for windows only.
Its the router you need to configure for port forwarding, not your operating system. 

You need to tell the router to take all of the traffic coming in on port xxxx and send it to computer xxxx. The website I posted will tell you how to do that. The only thing you may need to do in Ubuntu is set up a static IP. Do you know if your network uses DHCP to assign IP addresses or did you have to manually enter an IP address to get your Ubuntu machine on the network?

---

### Post by Atrio05 on 2007-06-19
our network uses DHCP. do i have to use static IP address id rather not.

---

### Post by cogadh on 2007-06-19
You will likely need to set a static IP only on the PC that will be receiving the torrent downloads. It's pretty much the only way a basic router network can find the right PC to send the torrent traffic to. Fortunately, Ubuntu has a pretty good GUI for making network changes. Do you need instruction on how to do that?

---

### Post by toecutter on 2007-06-19
> **cogadh said:**
> The only thing you may need to do in Ubuntu is set up a static IP. Do you know if your network uses DHCP to assign IP addresses or did you have to manually enter an IP address to get your Ubuntu machine on the network?

That website is great :) Could you share how to set a static IP address in Ubuntu please?

---

### Post by Atrio05 on 2007-06-19
> **cogadh said:**
> You will likely need to set a static IP only on the PC that will be receiving the torrent downloads. It's pretty much the only way a basic router network can find the right PC to send the torrent traffic to. Fortunately, Ubuntu has a pretty good GUI for making network changes. Do you need instruction on how to do that?

yes i would like to know how to setup a static ip in ubuntu if you could help with that it would be really great!

---

### Post by cogadh on 2007-06-19
I'll give you the GUI method and it will be based only on the Ubuntu environment, I currently don't have any of the other versions (Kubuntu, Xubuntu) available to me.

You will need to gather some info from your router first. The router should have some kind of status page that shows your local network configuration and the internet configuration. Find the router's local IP address (not it's internet address) and make note of it. It will usually be some variation of 192.168.###.1. Next look for a section that tells you the IP addresses of your DNS servers and make note of them. Lastly, you will need the IP address that you decided to forward the port to. It should be an IP that has the same first three numbers (octets) as the router's local IP, but with a last octet that is different. I usually use 100 or higher (but no higher than 254). Now you have enough info to set a static IP on your machine:

[LIST=1]
[*]Click on System > Administration > Network (not Network Tools)
[*]Enter your password when prompted
[*]Choose your connection from the list and click Properties
[*]Change the Configuration setting from "Automatic configuration (DHCP)" to "Static IP address"
[*]Enter the IP address you chose as your machine's address and hit tab (The Subnet Mask will automatically fill in with 255.255.255.0, don't change it)
[*]Enter the router's local IP address in the "Gateway address" field and click OK
[/list]
Your network will briefly disconnect and reconnect. Now switch to the DNS tab. Under DNS Servers, click the "Add" button and type the IP address of your DNS server that you got from your router. Repeat for each DNS server entry your router had.

You will now be running with a static local IP and port forwarding should be sending torrent traffic directly to that machine. If you want to go back to DHCP, just fire up the Network tool again and change your connection properties back to DHCP.

---

### Post by firstlife on 2007-06-19
Azureus usually always does this, but one thing that really helps with torrents is setting the port between 49125 and 65535. You get much better downloads. ISPs block the lower ones to bittorrent.

About the firewall, see the Azureus Wiki
[http://azureuswiki.com/index.php/NAT#Port_Forwarding_on_Linux.2C_specifically_Ubuntu](http://azureuswiki.com/index.php/NAT#Port_Forwarding_on_Linux.2C_specifically_Ubuntu)

I recommend just adding these lines to you /etc/rc.local file:
/sbin/iptables -I INPUT 1 -i <EXT_INT> -p tcp --tcp-flags SYN,RST,ACK SYN --dport <PORT> -m state --state NEW -j ACCEPT 
/sbin/iptables -I INPUT 1 -i <EXT_INT> -p udp --dport <PORT> -m state --state NEW -j ACCEPT

where:
<EXT_INT> is external interface (e.g. 'eth0')
<PORT> is tcp port setup in azureus 

(see [http://azureuswiki.com/index.php/Firewalling#Open_Source_Operating_Systems](http://azureuswiki.com/index.php/Firewalling#Open_Source_Operating_Systems))

In my past experience with azureus, this gave the green smiles better than any graphical firewall manager.

---

### Post by Atrio05 on 2007-06-19
ok i'm gonna need help getting the information from the router because i tryed it and i guess i did it wrong because it did not work.

---

### Post by Atrio05 on 2007-06-20
when i set it up yesterday i got everything it asked to get the static ip and it didnt work. i couldn't go anywhere on the internet. i need help on the prescise things i need ti get i had a hard time finding the dns server ip and the actual ip of the router (do you mean the lan ip?)

---

### Post by Atrio05 on 2007-06-21
bump! :D

---

### Post by Atrio05 on 2007-06-21
bump

---

### Post by Atrio05 on 2007-06-22
still looking for a solution here! bump bump bumpity bump! :o

---

### Post by Atrio05 on 2007-06-23
help me please!!!!!

---

### Post by eggdeng on 2007-06-23
Assuming you have set up the static IP, try to ping an external address, for example
```
ping 83.25.236.110
```
If it works, your static IP is set up OK and it's a DCHP problem.

---

### Post by Atrio05 on 2007-06-26
so what do i do if it's a dhcp problem?

---

### Post by eggdeng on 2007-06-27
Cross that one when you come to it.

---

### Post by stchman on 2007-06-27
> **Atrio05 said:**
> the only help on there is for windows only.

You setup the router through a web browser.  All is the same.

In windows I type in 192.168.1.1 in a web browser.  In Linux I type 192.168.1.1 in a web browser.

See, all is the same.

---

