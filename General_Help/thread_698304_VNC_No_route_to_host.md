---
title: "VNC No route to host"
date: 2008-02-16
forum: General Help
---

### Post by milan2008 on 2008-02-16
I followed the instructions to enable Ubuntu Remote Desktop.I unchecked Ask for confirmation and entered a password on the server.The server is 1 KM away.It is Xeon and has Gutsy.

When I try to access the server from my PC(Pentium D,Feisty): vncviewer ----serverip----
It shows this:
No route to host

How can I set up properly VNC Remote Desktop?

Thanks in advance.

---

### Post by SpaceTeddy on 2008-02-16
"no route to host" means that your computer cannot find the remote computer at all. It does not indicate a VNC problem, but a routing problem, i.e. the packets you are sending being bounced back to you with a "receiver cannot be contacted"

either something your side or on the remote sites routing setting is set wrong... does the remote site use nat ??? what is your setup ?

---

### Post by milan2008 on 2008-02-16
I have TOR and Privoxy on my Pentium D.Maybe it is the problem?

---

### Post by SpaceTeddy on 2008-02-16
mhm... maybe...try turning them off and see what happens... 
otherwise, i really need the setup with ip-addresses to help you... 

also, can you access other services on the remote maschine... like ssh for example ?

---

### Post by milan2008 on 2008-02-17
When I tried SSH it also says no route to host.
Both PCs have ADSL connections and I think they are static because when I restart the ADSL on each PC the IPs remain the same.On my PC it is 192.168.1.3 and on the other one 192.168.1.4
I am using ADSL over ethernet on both machines.

---

### Post by Keith Hedger on 2008-02-17
You may have to open the port for vnc on your machines (usually port 5900 ), I would using suggest firestarter to allow connections from your pc through the firewall

---

### Post by SpaceTeddy on 2008-02-17
ok... this will be a longer one - i fear :)

if you say you have adsl on both sides (you and remote) you will have something that connects to the dsl... i would suspect that is a router or something similar (at any side itmaybe it is a fully grown computer which acts as firewall/router). Anyway, you will need to figure out the IP adresses which your ISP gave you (this is only for the site you are trying to connect to..) and put a port forwarding there so that you can access the remote internal computer.

Here is how i understand your setup

You <---> ADSL Connection 1 <---> Internet <---> ADSL Connection 2 <---> VNC Server

Each ADSL Connection will have an IP address assigned to the hardware that is connectiong to it. This is NOT something that starts with 192.168.x.x ,since those ranges are strictly for private use and are not assigned to anything in the Internet.

if you are unsure what your assigned IP address is, use [this]("http://www.whatsmyip.org/") link to see what you have been assigned. i would bet that the IP adress displayed on the page does NOT correspond with the IP address you have assigned to your computer.

from now on, i will only talk about the server side, meaning i will talk about the adsl connection 2 and the VNC server. The rest is of no improtance and no concern to the setup.

first off, you will need to figure out if the IP address of the ADSL connection changes. Lots of ISP have a daily reconnect where they assign new IP's, so people don't go around and build their own server. You can check that using the page for your IP address at the site of the server, then disconnect the modem for a while, reconnect it and check your IP again. If they differ, you have dynamic IP addresses. 

How to get around Dynamic Addresses. Only do this if you really have dynamic IP addresses. Howto setup dynamic hostnames can be found at [http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html]("http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html")

after you know either your fixed IP address, or the hostname you need to connect to, the last thing is port forwarding which need to be setup. This means that the little box that between the server and the internet, the one that handles the ADSL connection, need to know that it shall forward traffic that is directed to it to an internal host.
VNC uses port 5900 (as stated before) and ssh uses port 22 (both TCP). How to setup the port forwarding i cannot help you, since ther variety of hardware for that is way too big.

One last thing - i would NOT open a VNC port directly to the Internet... since i am not sure how secure it is and if it is encrypted... but for testing purposes it is enough.

i hope you can follow by blabber... and that it works :)

---

### Post by Keith Hedger on 2008-02-17
Yes I agree I would not open the vnc port to every one but u can specify a
single ip address in firestarter, also i beleive you can use vnc over ssh ( not sure how to do this, search the forums) which would be MUCH safer, I dont use vnc anymore so i cant test this.

---

### Post by SpaceTeddy on 2008-02-17
**<OffTopic>**

No, you cannot specify a single IP if you have a dynamic IP assigned from your ISP, since your IP always changes then and you cannot pin it down to one.
Furthermore, the more services you run, the more vulnerable your system gets. So just restricting the IP's does not mean that all security holes are patched... 

as for vnc over ssh. open a ssh session with this command
> ssh -L 5900:localhost:5900 user@remotehost
while replacing the user@remotehost with the correct username and hostname and you can connect to the remote vnc server by connecting to your local machine (i.e. tell vnc to connect to localhost:5900). this only works if you do NOT have a vnc running on your local machine
**</OffTopic>**

---

