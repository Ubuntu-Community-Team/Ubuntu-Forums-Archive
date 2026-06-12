---
title: "Port forwarding issue"
date: 2008-07-07
forum: General Help
---

### Post by ybd on 2008-07-07
Hey.
I'm trying to open my ports for BitTorrent purposes but it just doesn't seem to work.
I'm got a wireless router that I am easily to open ports with under Windows XP, however despite despite forwarding them correctly through the Router, the ports are always closed under Ubuntu. Tried multiple ports in the 50000-65535 range, none seem to work.
Also tried this page:
[http://www.linuxquestions.org/questions/linux-security-4/how-to-open-ports-in-ubuntu-451282/](http://www.linuxquestions.org/questions/linux-security-4/how-to-open-ports-in-ubuntu-451282/)
And also tried disabling the Ubuntu firewall with "ufw disable" under root. 
Still the port is apparently closed. I'd appreciate any help on this :)

---

### Post by jw5801 on 2008-07-07
Port forwarding has nothing to do with your computer it's all through your router. The firewall isn't set up by default in Ubuntu, so you shouldn't have any trouble. What are you using to test whether the port is open?

---

### Post by ybd on 2008-07-07
> **jw5801 said:**
> Port forwarding has nothing to do with your computer it's all through your router. The firewall isn't set up by default in Ubuntu, so you shouldn't have any trouble. What are you using to test whether the port is open?

I tried a few web-based sites to probe the port, including ShieldsUp. Also tried Azureus's checker that is build into the program.
ShieldsUp reports the port as 'Stealth' while other checkers report it as closed.
I tried using FireStarter to open the port - it didn't work.

---

### Post by jw5801 on 2008-07-07
> **ybd said:**
> I tried a few web-based sites to probe the port, including ShieldsUp. Also tried Azureus's checker that is build into the program.
ShieldsUp reports the port as 'Stealth' while other checkers report it as closed.
I tried using FireStarter to open the port - it didn't work.

Unless you've started firestarter at some stage, it won't be running anyway, so that's not going to help. Are you forwarding to the right IP? Sure you're not getting a different IP in Ubuntu to the one you're getting in XP?

---

### Post by ybd on 2008-07-07
Yes, DHCP is on and the IP is definitely correct.

---

### Post by ybd on 2008-07-07
Anyone?

---

### Post by Claus7 on 2008-07-07
Hello,

in order for some programs to work, they need one to forward the ports both to one's firewall and one's rooter.

You say that you are able to do this via windows, so you are able from there to do port forwarding.
You also said that you were able to do that with firestarter.
Now do these simultaneously in ubuntu. What I mean is open your pc, go to firestarter and allow the ports you want. Then go to your browser, connect to your router and forward the ports you want. Click apply and save. Then see if this works or not.

I'm telling you all these, because I have to select, via my browser, the ports I want to forward almost every time I open my computer.

Just FYI I give you this link:
[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)
you can follow this procedure to open the ones you want. 

Hope this helped,
Regards!

---

### Post by blackhatbrigade on 2008-07-07
I couldn't tell by looking at it, but does firestarter just use iptables to firewall the system?  The only reason I ask, is that if he's still having problems he can give us the output from "iptables -L" which would make it easier to figure out what's going on.

---

### Post by ybd on 2008-07-07
> **blackhatbrigade said:**
> I couldn't tell by looking at it, but does firestarter just use iptables to firewall the system?  The only reason I ask, is that if he's still having problems he can give us the output from "iptables -L" which would make it easier to figure out what's going on.

Here's the result of "iptables -L": (note that I'm trying to forward port 60312, and that that FireStarter was down when I put in the command)
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  SL2141.home          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  SL2141.home          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             10.255.255.255      
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             10.0.0.1            
INBOUND    all  --  anywhere             10.0.0.1            
INBOUND    all  --  anywhere             10.255.255.255      
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
ACCEPT     tcp  --  anywhere             10.0.0.1            tcp dpt:60312 
ACCEPT     udp  --  anywhere             10.0.0.1            udp dpt:60312 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             10.0.0.0/8          state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             10.0.0.0/8          state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.0.0.1             SL2141.home         tcp dpt:domain 
ACCEPT     udp  --  10.0.0.1             SL2141.home         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  10.0.0.2             anywhere            
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere    
```

So yeah... it says that it accepts 60312 but it just doesn't seem to work

---

### Post by roy82 on 2008-07-07
I have the same problem, trying to do port forwarding.. i had already port forward in my router, but the port 61234 still closed after checking..
below is also my iptables

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55000 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
roy@roy-desktop:~$ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 61234 -j ACCEPT
roy@roy-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61234 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
roy@roy-desktop:~$ sudo iptables -A FORWARD -p tcp -d 0/0 -s 0/0 --dport 61234 -j ACCEPT
roy@roy-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:55000 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61234 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61234 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by blackhatbrigade on 2008-07-07
That's the firewall on your system right?  And I take it 10.0.0.1 is the ip in your network?

If that's your system and you're trying to receive that port, then I don't think forward is the correct chain for that.  Although, to be honest, the: "ACCEPT     all  --  anywhere             anywhere" in your INPUT chain should allow that port to come in.

Try "iptables -P INPUT ACCEPT"

That'll open up your system to all incoming connections.  So just use it to test, then do "iptables -P INPUT DROP" to get it back to where it is now.

let me know if that works or not.

---

### Post by ybd on 2008-07-07
> **blackhatbrigade said:**
> let me know if that works or not.

Yes, 10.0.0.1 is my network IP (the one provided by DHCP).
Well after doing INPUT ACCEPT, oddly enough, the ports are still unconnectable. This is weird.

---

### Post by blackhatbrigade on 2008-07-07
Personally (that's my disclaimer for my opinion :) ), if you're behind a router that you're selectively forwarding ports on (read, NOT DMZ), you don't have to worry about attacks from your local network or are the only system in your network, then I wouldn't use firestarter at all.  That is my opinion, which you can be sure not everyone agrees with.

Having said that, I would personally just flush the INPUT, FORWARD and OUTPUT chains, set them all to ACCEPT, and remove the other chains.  If you want to lock down your system I'd suggest learning a little more about iptables, changing the policies to DROP and then opening holes for what you want.  It's a whole lot cleaner looking and easier to read than what firestarter is doing.

But that's just my opinion.  If you want to try it I can put down the commands to wipe out what firestarter has done and open it all up.  But I would ONLY suggest that if your router is only forwarding what you want to your system (and isn't set to forward DMZ or massive port ranges to your system).

---

### Post by ybd on 2008-07-07
Yeah, the only reason I installed Firestarter in the first place is to use it as something like a GUI to the iptable so that I could open that port... I didn't need the firewall aspect of it.

> **blackhatbrigade said:**
> If you want to try it I can put down the commands to wipe out what firestarter has done and open it all up.

Yeah, that would be nice, thanks. Hopefully I can it to work that way.

---

### Post by blackhatbrigade on 2008-07-07
You should probably uninstall firestarter first.  I would imagine the easiest way to do that would be through the package manager.

iptables -F INPUT
iptables -F FORWARD
iptables -F OUTPUT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -X <custom chain>

The first six straighten out the default chains.  You also have some custom made chains that firestarter made which you'll need to just remove.  That is done with the 7th command.  You'll need to use it for each of the custom chains.  You can tell the custom chains after you do the first 6 commands by typing "iptables -L" and seeing what chains are there that have rules to them still.  Just replace the <custom chain> with the name of the chains.

That will completely remove any firewall whatsoever and you'll be open to accept connections from anything.  Again, just make sure your sparing with what you pass to it through the router.  If you're still not getting a connection after this then the problem is in your router.  You'll need to double check everything in the port forwarding there (especially if you're on DHCP)

let me know how that works

---

### Post by ybd on 2008-07-07
Holy crap it works! Yeaaaaah! You have no idea how long this has been bothering me.
Thank you so much man.

---

### Post by blackhatbrigade on 2008-07-07
;) Stay away from those nasty firewall programs.

Actually, it's really not that hard to setup your own iptables rules.  Just takes a little bit of research.

One last thing, be sure those changes stick.  I forget if you need to set that up in some startup config file or something.  Would be a good question for someone that knows more about it than me. :)

---

### Post by roy82 on 2008-07-07
```


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain INBOUND (0 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61234 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:61234 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (2 references)
target     prot opt source               destination         

Chain LSI (1 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (0 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere     


```

I can't remove the chains....
Hmmm..sorry it still does not work for me...

However i discovered that the ipaddress that deluge reported with the test thingy is different with my ipaddress that is reported under "status" of my linkysys router...

i am using deluge.

Is that the problem?
and how can i resolved that?
Please help...

---

### Post by roy82 on 2008-07-07
This is really strange just now i used the utorrent port checker and it actually report that i can received connections thru that port.

i realised that utorrent is actually reporting the correct my external ip address (same as in my router)

But how could this be? i tot i only got 1 external IP? 
How can i change the intepreted ip address in ubuntu? it seems that ubuntu is noting a wrong ip as its external ip?

Sorry maybe i am confusing you but it is actually confusing me too

---

### Post by blackhatbrigade on 2008-07-07
You'll need to do:

iptables -X INBOUND
iptables -X LOG_FILTER
etc... for each of those extra chains

The ip address in the Status part of your router will either be the Gateway IP (the address of your router on your internal network) or the WAN IP (ip address to the rest of the world).  I have no clue what deluge is reporting, but I'd imagine it should be your WAN address.

---

### Post by roy82 on 2008-07-07
```

roy@roy-desktop:~$ sudo iptables -X LOG_FILTER
iptables: Too many links
roy@roy-desktop:~$ sudo iptables -X LOG_FILTER
iptables: Too many links
roy@roy-desktop:~$ sudo iptables -X INBOUND
iptables: Too many links
roy@roy-desktop:~$ sudo iptables -X OUTBOUND
iptables: Too many links

```


i can't remove, the above state the error :(

---

### Post by blackhatbrigade on 2008-07-07
You have several addresses going on, even with a simple System->Router->Inet setup.  You'll have a internet address which your router carries, A gateway address (which is the internal address for your router) and each system in your network will have it's own internal address.  Even though the address to your computer is the internal IP, programs can find out what the Internet IP is (for example, you can go to [www.whatismyip.com](www.whatismyip.com) and see what webpages see you as).  What it boils down to is what certain applications/websites can see.  Anything outside of your network will not see your internal network addresses (well, for our discussion we'll assume this is right).  It sounds complicated but once you get a handle on it, it's really not.

---

### Post by blackhatbrigade on 2008-07-07
Try flushing them first...

iptables -F <chain name>

---

### Post by roy82 on 2008-07-07
Sorry,

let me explain again 

utorrent 218.212.XX.XX -->Correct (same as my router)
defuge 218.186.XX.XX -- >Wrong (Dun know where defuge get from)

yah....for utorrent it works..which means port is forwarded correctly

thanks

---

### Post by roy82 on 2008-07-07
Sorry failed again, unable to flush

```

roy@roy-desktop:~$ sudo iptables -F LOG_FILTER
roy@roy-desktop:~$ sudo iptables -X LOG_FILTER
iptables: Too many links


```

---

### Post by blackhatbrigade on 2008-07-07
Don't know... maybe restart defuge?  I don't know why it'd be getting a different IP.

Port forwarding is working now?  Great! :D

---

### Post by blackhatbrigade on 2008-07-07
Use "iptables -X <chain>" on the listings with 0 references first (sorry, my brain shut down for a couple there).

---

### Post by roy82 on 2008-07-07
Errmmm...but i am using defuge....


[http://www.utorrent.com:16000/testport2.php?port=61234](http://www.utorrent.com:16000/testport2.php?port=61234) why does this website report my correct Ip

and 

[http://www.deluge-torrent.org/test-port.php?port=61234](http://www.deluge-torrent.org/test-port.php?port=61234) report my wrong ip?
can you try?

i am sorry...it is working but i can't use it...

:(

---

### Post by blackhatbrigade on 2008-07-07
My IP shows up correct on both.  I have no clue why it would be wrong for you.  Did you try refreshing both pages?  Also, you don't by chance have a dual WAN router at work?  something like: [http://images.tigerdirect.com/itemdetails/H950-1022-out-wg.jpg](http://images.tigerdirect.com/itemdetails/H950-1022-out-wg.jpg) maybe?

That's the only thing I could think of.

---

### Post by roy82 on 2008-07-07
i still unable to flush and delete below is the log

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  dns8.maxonline.com.sg  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns8.maxonline.com.sg  anywhere            
ACCEPT     tcp  --  dns3.maxonline.com.sg  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns3.maxonline.com.sg  anywhere            
ACCEPT     tcp  --  dns9.maxonline.com.sg  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  dns9.maxonline.com.sg  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
^[[A^[[BDROP       all  --  255.255.255.255      anywhere            

DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.101        dns8.maxonline.com.sg tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        dns8.maxonline.com.sg udp dpt:domain 
ACCEPT     tcp  --  192.168.1.101        dns3.maxonline.com.sg tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        dns3.maxonline.com.sg udp dpt:domain 
ACCEPT     tcp  --  192.168.1.101        dns9.maxonline.com.sg tcp dpt:domain 
ACCEPT     udp  --  192.168.1.101        dns9.maxonline.com.sg udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:61234 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:61234 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (4 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain OUTBOUND (1 references)
target     prot opt source               destination         
roy@roy-desktop:~$ 
roy@roy-desktop:~$ sudo iptables -F OUTBOUND
roy@roy-desktop:~$ sudo iptables -X OUTBOUND
iptables: Too many links
roy@roy-desktop:~$ sudo iptables -F LOG_FILTER
roy@roy-desktop:~$ sudo iptables -X LOG_FILTER
iptables: Too many links
roy@roy-desktop:~$ sudo iptables -F INBOUND
roy@roy-desktop:~$ sudo iptables -X INBOUND

```


nope i only got 1 wan.
i am using WRT54G linksys router

---

### Post by blackhatbrigade on 2008-07-07
Did you uninstall your firewall program?  It looks like all your chains are back.

---

### Post by roy82 on 2008-07-07
i really do not know why i can have 2 different IP....

it is really amazing...

lol...

and i think that is the cause of the problems becoz...i am port fowarding of a IP address that my defuge is not recognising

---

### Post by blackhatbrigade on 2008-07-07
1 problem at a time.

First, it looks like your firewall program is still installed.  All of the rules for your input, forward and output chains are back.  Which usually means your firewall checked up on your iptables config and saw what we did.  Then, in it's mind, corrected it.  This means you'll need to uninstall the firewall program and redo the commands I posted before.  After that you should be able to delete the custom chains (starting with the ones with 0 references).

Second, we should be able to fix the multiple ip listings by shutting down everything (modem, router and PC) and then bringing it all back up.  That's if removing the firewall stuff doesn't fix it (it very well might be messing up your ip for defuge, but that's just a guess).

Start there and see what happens.

---

### Post by roy82 on 2008-07-07
I got D/c and i restarted my com. But i uninstall firestarter
is the below correct?


```

roy@roy-desktop:~$ sudo iptables -L
[sudo] password for roy: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
roy@roy-desktop:~$ 

```

---

### Post by roy82 on 2008-07-07
it still doesn't works

yah i go shutdown everything...

However i thank you for your patience. 
I appreciate it very much :)

---

### Post by roy82 on 2008-07-07
i restarted ...still having 2 diff IP...:(

---

### Post by blackhatbrigade on 2008-07-07
That is what iptables -L should look like.

Ok, so after restarting everything it still shows you having two different IP's?

Does utorrent still work ok?

---

### Post by roy82 on 2008-07-07
yah utorrent works ok..
guess i have to look for another client?

---

### Post by blackhatbrigade on 2008-07-07
well, I've been looking at deluge to try and figure it out (didn't know it existed until you mentioned it).  But the thing that bothers me is that you said you could go to two different ip reporting websites and one reported a different ip than the other?  Or is it just deluge reporting the erroneous ip?

---

### Post by roy82 on 2008-07-07
is 2 different ip reporting sites...becoz i do not know the connection between the defuge and the reporting websites (maybe defuge send my ip to that website) or maybe is that website that get my ip..i dunnoe whether u understand..

---

### Post by roy82 on 2008-07-07
actually...maybe my port forwarding is alrite? just that when i use defuge port checker it give me an error but i tried some other port checkers, it seems that my port forwarding is ok.. or maybe is defuge website erroneous?

---

### Post by blackhatbrigade on 2008-07-07
My guess would be that deluge is trying to use a proxy?  You'd have to check the settings, but that's the only explaination I can think of.  Maybe someone else can think of what else could be causing that.

---

