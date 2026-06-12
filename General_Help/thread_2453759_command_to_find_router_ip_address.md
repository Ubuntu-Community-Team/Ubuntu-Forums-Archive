---
title: "command to find router ip address ?"
date: 2020-11-16
forum: General Help
---

### Post by garyed on 2020-11-16
Is there is a command in Ubuntu that would tell anything about a router that is being used as an extender? 
Here's my situation,
I have two TP Link wireless routers wired together. The first one is the main one connected to my cable internet & the second one is wired to that one as an extender. The first one is not a problem to access because I use the typical 192.168.0.1  default gateway to access & check or change all my settings. The second one in order to make it work as an extender I disabled DHCP  & changed the default gateway. I did that about two years ago & I can't remember the default gateway that I used. I used to access it from my desktop to check or change settings but I need to know the address & I'm not sure if it's 192.168..0.x or 192.168.1.x. Nothing on my main router tells me about the secondary router so I'm at a loss. I tried plugging my laptop into the secondary router & that didn't help.
I don't want to have to do a factory reset if I can help it. Is there any terminal command that might help?

---

### Post by SeijiSensei on 2020-11-16
Try installing nmap and doing a ping scan of the networks:
```
sudo apt install nmap
nmap -sP 192.168.1.0/24

```
will try every IP from 192.168.1.1 to 192.168.1.254.

---

### Post by TheFu on 2020-11-16
[LIST]
[*]arp
[*]nmap -sT {subnet/24}
[*]traceroute if the device is using the 2nd router to connect to the 1st router.
[/LIST]

It is a good idea to write network info on a 3x5 card and use painters tape to put it on the different network devices.
For a router, that info should be:
[LIST]
[*]wan ip/network
[*]lan IP/network
[*]gateway
[*]login account and ... which password manager db has the password for the different accounts.
[/LIST]

---

### Post by garyed on 2020-11-16
> **SeijiSensei said:**
> Try installing nmap and doing a ping scan of the networks:
```
sudo apt install nmap
nmap -sP 192.168.1.0/24

```
will try every IP from 192.168.1.1 to 192.168.1.254.

i tried that & all I got back was:
Starting Nmap 7.60 ( [https://nmap.org](https://nmap.org) ) at 2020-11-16 21:01 EST
Nmap done: 256 IP addresses (0 hosts up) scanned in 104.16 seconds

---

### Post by oldfred on 2020-11-16
Second router
[https://www.linksys.com/ca/support-article/?articleNum=155108](https://www.linksys.com/ca/support-article/?articleNum=155108)
Did you do LAN to LAN or LAN to WAN?
If you know settings on first, plug computer just into second router and check or change settings.

Do you have settings from first Router?
And then reconfigure second router as per video.

I just did this on my system LAN to LAN, but cheap Chinese router from cable vendor has different configuration and my Linksys is older so not quite the same.
My systems shows second router with nmap, but first router still shows it incorrectly, but it works.

Channel was auto chgd to 5
wireless mode Mixed b/g/n
SSID/Network name
Security mode: WPA2/WPAz-PSK-TKIPP/AES
IP: 192.168.1.1  I then used .2 on second router.
Tried with & without binding by MAC - without worked finally
But set DHCP to start at 3 and Linksys at 2
Still shows as 0000 in status, but nmap still shows and can log in to it

Second router
Channel 11
Advanced NAT (or router mode) off (could not find on mine)
Same Security mode: 
set to 192.168.1.2 network setup
Set SSID & password
Disable DHCP
save

---

### Post by garyed on 2020-11-17
I did LAN to LAN & set up the secondary router exactly as it was shown in the video except I don't know what address I changed the default gateway to . It's been working fine for a couple years but I want to get into the setup of the secondary router. Unless I can find the ip address that I changed it to, I'll probably have to do a factory reset to get into the setup if I can't figure out the ip address but I was hoping there was an easier way. Next time I'll know better to write the address down & tape it to the router.

---

### Post by oldfred on 2020-11-17
If LAN to LAN then should be .2 where main router is .1.
So check full setting on main router.

Once you change address on second router you have to use that to log into it as default does not work.
I thought I had changed it correct several times, but could not log in either new address or old login. So had to reset & start over.
And DHCP range overlapped .2 originally. Was not sure whether I had to add .2 as fixed on first router but have in DHCP as it then would know it was fixed. 
Or exclude from DHCP and then just set second router to .2, which then now seems to work.

---

### Post by ActionParsnip on 2020-11-17
```

#internal router IP
ip route show | head -n 1 | awk {'print $3'}

```
.
```

#External IP
wget -q -O - https:\\ip.keithscode.com`

```

Nice and easy

---

### Post by TheFu on 2020-11-17
> **ActionParsnip said:**
> ```

#internal router IP
ip route show | head -n 1 | awk {'print $3'}

``` 

This assumes a normal setup and is very handy for that.  I use an alias to make the 'ip' cmd prettier.
```
alias iproute='ip route | column -t'
```
Or the old cmd, **route -n** does this automatically.

But with a setup like this:
```
Internet -- Router1 -- Router2 -- computerB
                    |
                    +- computerA
```
ComputerA won't see Router2, but arp should see the WAN interface for Router2 ... assuming it is being used as a router.  But it could be used as a plain switch by ignoring the WAN port, setting the LAN IP for Router2 to be an unused, outside-the-DHCP range managed by Router1 ...  
I'll add a photo in a few minutes of the port connections.

---

### Post by TheFu on 2020-11-18
Attached is an image of a wifi/router that has been repurposed to be only a wifi-access point for guest use. The vendor stopped updating the firmware AND no 3rd party firmware like dd-wrt or openwrt is compatible.

The Blue RJ-45 is the WAN port. It is empty. Unused.

The Yellow RJ-45 ports are for the LAN. Only 1 port is used, which eventually connects back to the ISP-provided router and gets a DHCP-reserved IP from that ISP-router. That makes the IP effectively static.  I force a x.x.x.254 IP for it.  The .254 IP is outside the dynamic DHCP range provided to random devices.  This part of my network is outside any trusted network. I don't trust wifi unless a vpn or ssh is used.  If I didn't have this $130 when new device already, I'd get a $80 Ubiquiti AP. That's what I've deployed to clients and they work extremely well to get an AP where it is actually needed, not limited to where a wall power plug is available.

This router has almost all normal router services disabled. No DHCP. No DNS. 

Hopefully, this clarifies things and the image helps.

To expand my network between floors, I use a Powerline 600 Mbps setup - that's the claim on the box.  They have 1200 Mbps Powerline today. For my connections between 2 devices at each end, I'm seeing a stable 60+ Mbps bandwidth. YMMV.  If I were doing this today, I'd get a MoCa  2Gbps setup instead. This requires that COAX cable exist in the locations already, which is the case here.  Moca is supposed to actually provide the bandwidth claimed. Moca is more expensive, but over a 10-20 yr life, that $40 price difference really doesn't matter too much.  I'm not a fan of using wifi-to-wifi extenders.  I'm not a fan of wifi unless absolutely necessary.  In a prior job, I designed and deployed wifi for over 1200 locations and saw how local conditions could make that a nightmare for connectivity and unrealistic expectations.  In short, stay wired whenever possible.  And never trust any RF/wifi/BT for security.

To find RouterA ... it is just the default gateway in the **ip route** and **route -n** for any machines.
To find RouterB ... I use an nmap scan .... **sudo nmap -O  10.22.21.0/24**
The results are longer than I'll show here, but ... 
```
Nmap scan report for tp-link (10.22.21.254)
 90:F6:52:FF:FF:FF (Tp-link Technologies)
 OS CPE: cpe:/o:linux:linux_kernel:2.6.15
 OS details: Linux (likely TP-LINK WAP)
```
those are part of the output for the scan.  I have script that formats the scan output so I can find devices on the network that I've forgotten.  There's usually an extra r-pi somewhere. ;)  The system doing the scan is upstream from RouterB, not a client.  RouterB is on a different subnet than the other routerA connections in my world.

---

### Post by HermanAB on 2020-11-18
There are many ways to find the IP address.

For example:
1. Look on the back of the router on the label, for the MAC address.  Then log into your home router control panel and look at the DHCP address allocation.
2. Sniff the WiFi DHCP/DNS request data with *ettercap*.  Connect another laptop/tablet/phone to the extender.  Look at the DHCP and DNS request messages.

---

### Post by garyed on 2020-11-28
Sorry it took me so long to reply but i had some other personal things going on & I put everything on hold for a week or two. 
Anyways I'm still in the same spot because I already changed the ip address of the second router & disabled DHCP a couple years ago. 
My desktop is wired to my primary router & I thought I remembered connecting to my secondary router through my desktop.
When I access the setup on my primary router, I assumed my secondary router would show up as a wired client but it doesn't.     
Right now everything is still working & I am not in too much of a rush to get into the setup for now so I'm going to keep playing around as long as I can until I have to do a factory reset. 
I just keep thinking there has got to be a way to find the ip address I changed it to with some type of command but so far nothing has worked.

---

### Post by garyed on 2020-11-28
> **HermanAB said:**
> There are many ways to find the IP address.

For example:
1. Look on the back of the router on the label, for the MAC address.  Then log into your home router control panel and look at the DHCP address allocation.
2. Sniff the WiFi DHCP/DNS request data with *ettercap*.  Connect another laptop/tablet/phone to the extender.  Look at the DHCP and DNS request messages.

1 - I've already logged in to my main router & I have not been able to find any trace of the the secondary router anywhere. 
 It's direct wired to the main router but for some reason it's not showing up. It's definitely working because I use it for my TV 
My main router is a TP Link AC 1750 & my secondary is a TP Link AC750
 
2 - Can you elaborate on how to sniff the Wifi DHCP/DNCS request data or look at those messages with a laptop either wifi or wired.

---

### Post by garyed on 2020-12-11
An update,
I finally gave up & did a factory reset on the modem.
Set it back up & wrote down the ip address I changed it to in case I forget it again.
I appreciate all the ideas but nothing i tried seemed to work. 
I thought there would be an easy way to find the ip address of the secondary router that I had changed from factory default & disable DHCP but I guess I was wrong.
I started to try the 250 to 500 possibilities but that was assuming I changed only the last two digits to 0.x or 1.x so I gave up.

---

### Post by HermanAB on 2020-12-14
To find the address of your router:

The best way to view router data is probably:
$ route

The second easiest is:
$ cat /etc/resolv.conf

A DNS query will also reveal the router address:
$ dig [www.myahoo.com](www.myahoo.com)

You can also look at the ARP cache, which requires typing only 3 letters:
$ arp

---

### Post by TheFu on 2020-12-14
HermanAB - post #9 above shows why getting an internal router IP isn't so simple as getting an upstream router IP.
ComputerA looking for Router2 isn't as easy as ComputerB finding Router2.

---

### Post by garyed on 2020-12-15
> **HermanAB said:**
> To find the address of your router:

The best way to view router data is probably:
$ route

The second easiest is:
$ cat /etc/resolv.conf

A DNS query will also reveal the router address:
$ dig [www.myahoo.com](www.myahoo.com)

You can also look at the ARP cache, which requires typing only 3 letters:
$ arp

I tried everything that was suggested here & more but came up empty. Even my primary router would not list the ip address of the secondary router whether it was being used by another device or not. 
I think the problem is that once you set the secondary router up like an extender & disable DHCP, it becomes more like a junction box with wireless capabilities. Now that I know the secondary router's ip address, I can log into the setup wthout any problems.  
Eureka !!!  I just realized that the command  "arp" does work after fishing through a bunch of ip addresses, it did show the secondary router.  
That's good to know for the next time .

---

### Post by TheFu on 2020-12-15
> **garyed said:**
>  
Eureka !!!  I just realized that the command  "arp" does work after fishing through a bunch of ip addresses, it did show the secondary router.  
That's good to know for the next time .

So ... post #3 had the answer.
I'd be surprised if the nmap didn't show it as well.  I tested those commands against my 2nd router, configured as a bridge before posting them.

---

### Post by garyed on 2020-12-15
> **TheFu said:**
> So ... post #3 had the answer.
I'd be surprised if the nmap didn't show it as well.  I tested those commands against my 2nd router, configured as a bridge before posting them.
You're right, I must have either over looked the arp command or I could have used it & not tried the correct ip address because about 30 of them popped up.
I tried so many ip addresses I just can't remember but I would have thought if i used the arp command that I would have tried all 30 of them until i got the right one.
Knowing what the correct ip address is made it easy to spot now. Also I did try nmap & iproute commands but they didn't help.

Thanks again for the help

---

### Post by garyed on 2020-12-15
> **TheFu said:**
> So ... post #3 had the answer.
I'd be surprised if the nmap didn't show it as well.  I tested those commands against my 2nd router, configured as a bridge before posting them.

How is your secondary router configured? 
Does the primary router connect to the secondary router to LAN or WAN?
Is DHCP disabled? 
Maybe I used the wrong parameters for my system. 
With my default gateway being 192.168.0.1 on the primary router, what would be the exact parameters for the nmap command to find my secondary router ip address?

---

### Post by TheFu on 2020-12-15
> **garyed said:**
> How is your secondary router configured? 
Does the primary router connect to the secondary router to LAN or WAN?
Is DHCP disabled? 
Maybe I used the wrong parameters for my system. 
With my default gateway being 192.168.0.1 on the primary router, what would be the exact parameters for the nmap command to find my secondary router ip address?


Post #10 above?

---

### Post by garyed on 2020-12-15
> **TheFu said:**
> Post #10 above?

I remember viewing that post before & that looks exactly how i have mine setup. I just forgot that you had posted it. I have DHCP server disabled & I assume you do on yours too. 
I also remember running the nmap command exactly as you posted (copied & pasted ) it in post # 10 but just got "0 hosts up" after a couple minutes. I'm assuming I need different parameters but I have no idea what they should be.
Where do you get the 10.22.21.0/24  from?

---

### Post by TheFu on 2020-12-15
10.22.21.0/24 is one of my subnets, in CIDR format.

If you want to look on 192.168.0.0/24, use that instead.

I usually go out of my way to ensure people can't just copy/paste commands, so they actually need to understand what they are requesting.  Using 192.168.0.0/24 or 192.168.1.0/24 as subnets limits VPNs, so choosing odd networks is helpful since I won't likely be in a hotel/cafe/company with a 10.22.21.0/24 subnet.  It is a routing thing, necessary when running VPNs.

---

### Post by garyed on 2020-12-15
> **TheFu said:**
> 10.22.21.0/24 is one of my subnets, in CIDR format.

If you want to look on 192.168.0.0/24, use that instead.

I usually go out of my way to ensure people can't just copy/paste commands, so they actually need to understand what they are requesting.  Using 192.168.0.0/24 or 192.168.1.0/24 as subnets limits VPNs, so choosing odd networks is helpful since I won't likely be in a hotel/cafe/company with a 10.22.21.0/24 subnet.  It is a routing thing, necessary when running VPNs.

Thanks, that worked too. I should have known to ask you a few weeks ago whether those numbers would be different depending on my default gateway. 
I think the arp command works a little better for just trying to find the ip address, since it's faster, there's no parameters to remember & less info to sort through.

---

### Post by TheFu on 2020-12-15
> **garyed said:**
> Thanks, that worked too. I should have known to ask you a few weeks ago whether those numbers would be different depending on my default gateway. 
I think the arp command works a little better for just trying to find the ip address, since it's faster, there's no parameters to remember & less info to sort through.

arp only works if the desired system has as a connection of a sort to the system asking. That is the big limitation.
Understanding the commands is always important.

---

### Post by HermanAB on 2020-12-16
Actually, with a problem like this, I would use ettercap to MITM the whole network and then just sit and stare at the packets for a bit to get the IP addresses.  Something like $ ettercap -T -M arp // //

---

### Post by garyed on 2020-12-16
> **TheFu said:**
> arp only works if the desired system has as a connection of a sort to the system asking. That is the big limitation.
Understanding the commands is always important.

When you say a connection to the system asking , I'm not quite sure what you mean.
Does it mean that nmap retains connections in memory & displays them even if they're not connected at the time, where arp only sees whats actually connected at the moment?

---

### Post by TheFu on 2020-12-16
arp tables on every network port time out. If you want MAC (ethernet hardware) addresses to be in the arp-table, then the system you run arp on, must have "seen" the other device you are interested in.  MAC doesn't route, so the connection has to be within what true ethernet range.  Look that up. Learn a little about the 7-layers of networking.  With IPv4, it is at the "physical" layer - i.e. were direct connections happen.  I vaguely remember that IPv6 does something else.

If you want to learn this networking stuff at a home-user's level, there are lots of dry books and articles about it. Can't remember how I learned, then expanded that knowledge probably 50x over the years.  I do know that "Security Now" podcast did a 2-3 part "How the Internet Works" where about 90% of the knowledge was confirmed and 10% was new. Google can find the audio or transcript'ed text easily.

---

