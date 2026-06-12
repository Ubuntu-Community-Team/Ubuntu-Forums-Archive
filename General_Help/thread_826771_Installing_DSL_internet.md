---
title: "Installing DSL internet"
date: 2008-06-12
forum: General Help
---

### Post by AgentZ86 on 2008-06-12
Hi all

I've selling Ubuntu computers, and I have cable so the NIC connects and works great everytime on all these older computer.

I need help directing my customers to connect to DSL.

I'm not aware of how DSL works.

Does DSL dialup anything or is there user/passwords needed etc.

Basically I do not know how to direct them;as I've never connected to DSL.

The customers typically just connect the NIC to their DSL box I'm guessing.

If someone could please give me some details on how to direct this customer ?

Does DSL automatically give out IP addresses IE acting as the DHCP ? or does the NIC have to be configured manually ?

This is a standard home user installation and using Ubuntu 8.04

Please advise
Thanks
:popcorn:

---

### Post by cmnorton on 2008-06-12
In the most simple DSL environment, think of the DSL modem as two devices. My DSL modem can be configured to be simple router with a one port switch, no wireless.  (Edit: ) The second device is the actual modem that converts ethernet packets to and from DSL protocol.

The DSL modem usually has a web or other interface that allows configuration.  Configured this way, the DSL modem can provide DHCP addresses to its client. My modem is pretty old; newer ones may and probably do have a switch larger than one port.

Usually, two devices are sold or provided to the customer. The first device is a router -- which these days is almost always wireless -- including a four-port switch. The second device is the DSL modem. 

The wireless router can provide internet addresses by DHCP or the addresses can be static. Wireless routers are almost always configured with a web browser from the host, so it is useful to configure the router with an ethernet cable and worry about wireless once, you can get out to the internet. 

When a wireless router is used, the DSL modem is put into "passthrough" mode, which means it just acts as a device to convert ethernet packets into DSL protcol.

---

### Post by trevelyan on 2008-06-12
Seems to me he should be talking to his ISP instead. they have all the info about whether his setup has a static or dynamic ip and all the settings for that.

---

### Post by cmnorton on 2008-06-12
> **trevelyan said:**
> Seems to me he should be talking to his ISP instead. they have all the info about whether his setup has a static or dynamic ip and all the settings for that.

I agree with you, but a lot of ISPs will not speak with you if you mention Linux. At best, they can barely speak with you about setting things up in Windows; at least that is my experience.

---

### Post by x1a4 on 2008-06-12
Hi,

It all depends on the ISP.  A typical DSL provider will supply a DSL modem/router preconfigured, so that the only thing you have to do is hook it up, and once the PPP light is on the Internet is on.  

You should ask the ISP for at least three things: 
 - IP addresses of their DNS servers and add them in network settings. 
 - whether the connection supports IPv6 and if not disable it. 
 - does the ISP provide a proxy server, and if so its address & capabilities, and use network settings to set it up it.

---

### Post by AgentZ86 on 2008-06-13
> **cmnorton said:**
> I agree with you, but a lot of ISPs will not speak with you if you mention Linux. At best, they can barely speak with you about setting things up in Windows; at least that is my experience.

Yes this is my experience also, except with comcast was pretty helpful here in MD

but I recall in the past as soon as I mentioned linux they instantly said I'm sorry we don't support linux, and they would not even talk about it anymore even if it was a problem with their stuff LOL

Anyhow thanks

---

### Post by AgentZ86 on 2008-06-13
> **x1a4 said:**
> Hi,

It all depends on the ISP.  A typical DSL provider will supply a DSL modem/router preconfigured, so that the only thing you have to do is hook it up, and once the PPP light is on the Internet is on.  

You should ask the ISP for at least three things: 
 - IP addresses of their DNS servers and add them in network settings. 
 - whether the connection supports IPv6 and if not disable it. 
 - does the ISP provide a proxy server, and if so its address & capabilities, and use network settings to set it up it.


And were do you set these setting ? Since I've never had to do any of this with my internet, I'm not sure I can help my customers on this topic.

But I do need to learn this since I'm planning on selling lots of linux computers.

which most likely they will be using anything from dsl,cable,dialup.
I guess I need to learn to configure dialup also in the future.

I'm guessing I can just click the network icon in the top toolbar and manually configure from there.?

This brings up the network settings window ? is there where I would configure the computer for internet connections ?

I've never noticed this before, but looks like I can set everyting from within this network settings windows ?

Please confirm that this is where I would create a manual settings for both dsl and dialup connection to the internet ?

Thanks all

:guitar:

---

### Post by trevelyan on 2008-06-13
yes.. that's where you have to do it. for the info contact the ISP and you're set.

---

### Post by AgentZ86 on 2008-06-17
> **trevelyan said:**
> yes.. that's where you have to do it. for the info contact the ISP and you're set.

Got it, thanks
:guitar:

---

