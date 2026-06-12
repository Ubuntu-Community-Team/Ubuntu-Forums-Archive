---
title: "ssh-copy-id  from server wired to netwok to computer connected via wifi"
date: 2023-12-24
forum: General Help
---

### Post by Old Jimma on 2023-12-24
Hello Ubuntuers:

I'm in the process of copying ssh keys to some of my computers.

when I copy them to computers that are connected to my network with a cable, the files get transfered nicely.

However, when I try to copy them to computers that are connected via wifi, they won't copy!

How do I fix this?

Thanks,OJ

---

### Post by MAFoElffen on 2023-12-25
Can you ssh to them manually between those computers? Can they ping each other? Just making sure they have a route between them right?

---

### Post by Old Jimma on 2023-12-25
I can ping all computers connected to the network by a cable... except the one connected by wifi.

The method I used to find the IP address of the computer is from the paragraph entitled, **Check for internal network configuration from GUI** from the web page [HTML]https://linuxconfig.org/how-to-find-my-ip-address-on-ubuntu-22-04-jammy-jellyfish-linux[/HTML] that is entitled, > How to find my IP address on Ubuntu 22.04 Jammy Jellyfish Linux

---

### Post by MAFoElffen on 2023-12-25
One assumption of ssh kys is that ssh and it's keys are ip-to-ip and that the Ip address stays the same consistently... Meaning that you have set the IP address as a static IP address. If you do
```

ip a

```
Then you can use most guides for Ubuntu 18.04 and newer to set your IP address as static...

Do you need instructions or a link for instructions? [https://tecadmin.net/how-to-configure-static-ip-address-on-ubuntu-22-04/](https://tecadmin.net/how-to-configure-static-ip-address-on-ubuntu-22-04/)

---

### Post by Old Jimma on 2023-12-26
Hello MAFoElffen:

Thank you for you for your reply.

I have studied the approach you've described previous to making my post. Thank you for confirming that I'm on the right path.

In my study of that approach, a user must designate:[LIST]
[*]a valid address,
[*]a valid netmas address, and
[*]a valid gateway.
[*]
[/LIST]

I'm pretty sure I can't use my special random number generator that I use to bet on the ponys to designate these addresses, right?

I could nof find guidance on the WWW to make these three specifications. 

So, I'm stumped. Am I suposed to use the iPv4 address under the Wired > Details tab? Is that a good choice?

And how to choose a netmask and gateway address? Are they written in the stars of virgo following a full moon? 

Please forgive my light-heartedness about these issues. I do not mean disrespect.

However, what I do mean by my queries is: If there is anybody who can do irreperable harm in making these specifications, it is me.

If you would kindly provide guideance on making these specificaitons, I'd be good for coffee at my house when you're driving by.

Sincerely,
Old

---

### Post by MAFoElffen on 2023-12-26
Please show me this from both the start point PC, and the target PC on Wifi
```

ip a

```

---

### Post by Old Jimma on 2024-02-20
Hello MAFoElffen:

My sincere apologies for this very delayed response to your request.

You may recall my asking the forum for help with 
[LIST]
[*]doing a ssh-copy-id from a computer wired to my home network
[*]to computer connected to my network via wifi.
[*]
[/LIST]

You requested the results from [HTML]ip a[/HTML] for both computers. Here they are:

**Results of ip a from computer wired to my home network**
> 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 1c:83:41:33:29:6f brd ff:ff:ff:ff:ff:ff
    altname enp2s0
    inet 192.168.1.227/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 84000sec preferred_lft 84000sec
    inet6 2600:1700:1c02:61f0:ca4c:3f54:efb3:209c/64 scope global temporary dynamic 
       valid_lft 3268sec preferred_lft 3268sec
    inet6 2600:1700:1c02:61f0:48b0:5321:74bb:230/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0:6804:620b:b69d:3ee4/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0:c6cd:75c6:6ecd:eb28/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0:9509:8501:ca27:f0a9/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0:85b7:1d2e:4c3e:66a/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0:d8a3:5c92:eedd:2cf8/64 scope global temporary deprecated dynamic 
       valid_lft 3268sec preferred_lft 0sec
    inet6 2600:1700:1c02:61f0::48/128 scope global dynamic noprefixroute 
       valid_lft 2112sec preferred_lft 2112sec
    inet6 2600:1700:1c02:61f0:1112:19a1:a5e9:60ca/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3268sec preferred_lft 3268sec
    inet6 fe80::d101:6f47:a6cf:968a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 10:6f:d9:74:ca:a9 brd ff:ff:ff:ff:ff:ff
6: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1441 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.8.18.125/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::7d1e:3e14:9942:ed8c/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever



**Results of ip a from computer connected to my home network by wifi**
[QUOTE]
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b0:dc:ef:00:63:3d brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.167/22 brd 192.168.7.255 scope global dynamic noprefixroute wlp0s20f3
       valid_lft 11211sec preferred_lft 11211sec
    inet6 fe80::2bc8:8972:3b5a:fae3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1441 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.12.18.27/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::305:71b2:9756:ebf9/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever
[QUOTE]

When I issue the command
[QUOTE]
ssh-copy-id queenie@192.168.4.167
[QUOTE]
from the computer connected by wire, tht command just hangs there and never executes.

[B]The ultimate purpose of this is to backup the computer connected via wifi to the computer connected by wire using [B]
[QUOTE]
rsync --delete -az -essh queenie@192.168.4.167:/home/queenie/ /mnt/3TB_1/Friday
[QUOTE]
where "queenie" is the user home directory on the computer connected by wifi; and /mnt/3TB_1/Friday is the address on the compter connected by wire (a mounted volume)

Thank you!!
Old

---

### Post by btindie on 2024-02-23
Your wired and wireless networks are on different subnets - 192.168.1.0/24 vs 192.168.4.0/22 - they are connected aren't they?

One simple test you can do is to run a simple http server on a wireless device and see if you can access it via a device on the wired network.

Run the below on a device that's on the wireless network ```
python3 -m http.server
```
You should then be able to access it via a wired device, e.g. [http://192.168.4.167:8000](http://192.168.4.167:8000) that should give a list of files/directories. Use Ctrl+c to terminate it.

If that doesn't work then you may want to look into your network setup.

[LIST]
[*]Can another device connected via wireless access that URL?
[*]Are you running a firewall on your wireless device that is preventing access?
[*]If you run [FONT=system]ssh -v queenie@192.168.4.167[/FONT] does it show that it connects and prompt for a password?
[/LIST]

Also check your router config to make sure there's not an option turned on that prevents devices on the wired network accessing devices on the wireless network.

---

### Post by TheFu on 2024-02-23
Please use code tags, not quote tags when posting terminal output.

Seems your understanding of IPv4 networking isn't complete.  Listen or **read** the transcriptions of episodes 25-29 of the Security Now! podcast to firm up your skills.  Those episodes are titled "How the internet works" and there are 2 or 3 parts. Episode 25 is the first part.

---

### Post by Old Jimma on 2024-02-26
Hello Forum People:

I have
[LIST]
[*]a server that is connected to my home network via a wired connection,
[*]several other client computers that are connected to the home network via wired connections, and
[*]several servers **connected to my home network via wifi**.
[*]
[/LIST]

For each machine connected by wire to the network, I determined its IP address by going to Settings (the gear icon) > Network > Wired list > left click on the gear icon associated to the home network.

This procedure gave me the IPV4 address that I used in the [HTML]ssh-copy-id -f remote_username@ip_address[/HTML] command.

From there, I used [HTML]remote_username@ip_address[/HTML] and was able to log into each of the client computer connected to the network by wire.


**THIS PROCEDURE DID NOT WORK FOR  COMPUTERS CONNECTED VIA WIFI.**

Specifically, for each computer connected via wifi to the network, I determined eqch of those compters' IP addresses by going to Settings > Network > WIFI list > click on Network > WIFI > click on the gear icon associated with tne wifi network the computer is connected to.

And next, at the sever, I issue the command:  [HTML]ssh-copy-id -f remote_username@ip_address[/HTML] 

Lastly, to log into the client connected via wifi, I issue this command from the server: [HTML]remote_username@ip_address[/HTML]

... and I'm not able to log into the client. I get a message that says: > ssh: connect to host 192.168.4.167 port 22: Connection timed out

When I look in the .ssh directory on the client connected via wifi, there is nothing in the directory. It is evident that the  [HTML]ssh-copy-id -f remote_username@ip_address[/HTML]  did not work.

Can some one, please advise how to get this to work, please?

Thanks,
Old

---

### Post by TheFu on 2024-02-26
Last time you posted this question, it was pointed out that the wifi subnet was different from the wired subnet, so routing wasn't setup between the 2 networks.  Did you fix that?

If the systems cannot **ping** each other (both directions) then ssh won't work in the direction that the ping doesn't work.

I've never used the -f option.  Seems like a bad idea to use it.

---

### Post by Old Jimma on 2024-02-26
Hello TheFu:

Thanks again for your reply. You certainly have taken good care of me over the years.

> [Last time you posted this question, it was pointed out that the wifi subnet was different from the wired subnet, so routing wasn't setup between the 2 networks. Did you fix that?[/B]

**I think that something like that was suggested, and I didn't understand it, and consequently did not follow up on the suggestion.**

I still don't understand what "the wifi subnet was different from the wired subnet," so routing wasn't setup between the 2 networks" means, and don't know how to fix it.

Perhaps it has something to do with the fact that the wifi connection used may be the wifi  Eero wifi extenders I use, and that is what you mean that the subnets are different.

Here is the results of [HTML]ip a[/HTML] for the wired server:

> 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 1c:83:41:33:29:6f brd ff:ff:ff:ff:ff:ff
    altname enp2s0
    inet 192.168.1.227/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 73086sec preferred_lft 73086sec
    inet6 2600:1700:1c02:61f0::48/128 scope global dynamic noprefixroute 
       valid_lft 2370sec preferred_lft 2370sec
    inet6 2600:1700:1c02:61f0:110b:e63b:efc3:5a8d/64 scope global temporary dynamic 
       valid_lft 3433sec preferred_lft 3433sec
    inet6 2600:1700:1c02:61f0:1112:19a1:a5e9:60ca/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3433sec preferred_lft 3433sec
    inet6 fe80::d101:6f47:a6cf:968a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 10:6f:d9:74:ca:a9 brd ff:ff:ff:ff:ff:ff
4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1441 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.16.18.26/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::7b3:f228:b765:55ee/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever


and here is the [HTML]ip a[/HTML] for computers that use the Eero wifi

> 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp0s20f3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether b0:dc:ef:00:63:3d brd ff:ff:ff:ff:ff:ff
    inet 192.168.4.167/22 brd 192.168.7.255 scope global dynamic noprefixroute wlp0s20f3
       valid_lft 14336sec preferred_lft 14336sec
    inet6 fe80::2bc8:8972:3b5a:fae3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1441 qdisc fq_codel state UNKNOWN group default qlen 500
    link/none 
    inet 10.12.18.72/24 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::ae80:af58:9aef:d6c5/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever


Thanks,
Old

ps. I'm not sure what

---

### Post by Old Jimma on 2024-02-26
Hello again TheFu: I have to use a wifi extender in my house, otherwise, we don't get cell service in most of the house.

---

### Post by TheFu on 2024-02-26
> **Old Jimma said:**
> Hello again TheFu: I have to use a wifi extender in my house, otherwise, we don't get cell service in most of the house.

That doesn't mean you have to have routing issues between subnets or even that you need different subnets.

Perhaps powerline networking would be a better solution, assuming there are power plugs in the places you need network connections?  Powerline is a "bridge", which means it is invisible on the network. It doesn't add or change IPs or subnets for any traffic.  For your needs, I suspect a setup like this would be all you need:

[LIST]
[*]1 router
[*]1 or 2 dumb switches (5 or 8 port $20/ea)
[*]1 powerline kit to bridge the router to the other part of the house (I have a 600Mbps powerline kit - 2 nodes, but I think 1200 Mbps are cheaper these days).
[/LIST]
Connect a switch to the far end of the powerline adapter.
Connect the other powerline adapter to your router
Connect a second switch to the router, if you need more ethernet ports there.
Everything connected to the router or the switches will be on the same subnet. Simple.

If you don't understand IPv4 networking, you'll never get this working.
You can learn it and subnetting many different ways.  A few episodes of the Security Now! podcast (Eps 25 and the next few) are titled "how the internet works".  Read or listen to those until subnets make sense.  Then you can master your LAN and setup subnets that work across all your devices.

---

### Post by btindie on 2024-02-26
I suspect your Eero wifi extender may be doing NAT itself which would explain why wired clients can't access wireless clients behind it.

If you do as I suggested in your other thread and run the below on a **wired** client
```
python3 -m http.server
```
and then in your web browser or via [FONT=system]curl[/FONT] on a **wireless** client connect to [http://IP:8000](http://IP:8000) (replacing IP with the IP address of your **wired** client)

If you then look in the output on your wired client, it'll show the source IP address, which if your Eero wifi extender is doing NAT, will show an IP address in the 192.168.1.0/24 subnet and not the expected 192.168.4.0/22 subnet if it was routing.

You've got a couple of options.
1) Disable NAT on your Eero wifi extender to put it into routing mode and add a route on your Router to the subnet your wireless network (192.168.4.0/22) is on via the IP address of your Eero wifi extender - you'd want to give that a static IP.
2) which is probably the easiest, put your Eero wifi extender into [Bridge mode]("https://www.howtogeek.com/289542/how-to-use-the-eero-in-bridge-mode-to-keep-your-routers-advanced-features/").
See also [https://support.eero.com/hc/en-us/articles/207621056-How-do-I-set-up-my-eero-if-I-want-to-keep-my-existing-router](https://support.eero.com/hc/en-us/articles/207621056-How-do-I-set-up-my-eero-if-I-want-to-keep-my-existing-router)
and to put your **router** into bridge mode see [https://support.eero.com/hc/en-us/articles/207613176-How-do-I-bridge-my-modem-router-combo-device](https://support.eero.com/hc/en-us/articles/207613176-How-do-I-bridge-my-modem-router-combo-device)

---

### Post by TheFu on 2024-02-26
If you setup the wifi-extender to be in bridge mode, which is how those things should be setup for most people, then everything should be on the same subnet.  However, network performance of wifi-extenders that don't use wired ethernet means the bandwidth has to be split between the other wifi router and all the clients.

I see no reason to use a web server at all. This doesn't provide anything that **ip address** on the system provides.

---

### Post by Old Jimma on 2024-02-27
Hi TheFu and Btinde:

Thanks so much for your considered advice and suggestions. I do appreciate them.

I've read, and re-read, and re-read them.

The remark from TheFu that I understood was> **If you don't understand IPv4 networking, you'll never get this working.**

Amen!!

I realized that I'm way over my head here, and needed a simple bone-head solution.

So, here is my bone-head approach to this:
[LIST]
[*]dig out one of my raspberry pis that is doing nothing right now,
[*]configure that pi to be on the wifi network that all of the other computers that are on wifi are on,
[*]turn that pi into the server that backs up those computers.
[*]
[/LIST]

That's  my bone-head, style of home networking.

I hope you will please put away your sling shot, and decide not to hunt me down for being a bone head. Some people like me are just that way. Just born that way

So, thanks for all your work. If you live in the Atlanta Metro area and want a reward of some sort, let me know. You deserve it!

Sincerely,
Old

---

### Post by TheFu on 2024-02-27
> **Old Jimma said:**
>  
So, thanks for all your work. If you live in the Atlanta Metro area and want a reward of some sort, let me know. You deserve it!

You should attend some of the ALE meetups!  Lots of people there want to help. There are weekly virtual meetings - online.

---

### Post by slickymaster on 2024-02-27
Threads merged

---

### Post by ActionParsnip on 2024-02-27
Can you SSH to the remote system in the traditional way? Does that work OK?

---

