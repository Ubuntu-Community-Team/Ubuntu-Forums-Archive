---
title: "Emergency Remote Access?"
date: 2021-08-26
forum: General Help
---

### Post by rsteinmetz70112 on 2021-08-26
I have a remote location that is sometimes unmanned.   Occasionally I lose contact with the servers there and can't do any checking to find out what the problem is. Can anyone suggest a reasonable alternate method to circumvent the problem?  

This morning no one is there. I have determined the phones work and there is power. But I can't contact any of the servers. This may mean out internet service is down or the servers are down. I've checked the ISP and they indicate an issue with the router/gateway by provide little information.

I suppose I could set up an old dial up modem to allow me to log into one or more of the servers, but I've forgotten how to do that.

---

### Post by HermanAB on 2021-08-26
I would get a standalone serial modem off Ebay, then forward a console to a serial port on a Raspberry Pi running Raspbian.

---

### Post by TheFu on 2021-08-26
If the ISP can't remote-reboot the modem/router, that isn't good.

You could setup a "clapper" (from the old TV commercials), then have an internet ping script run every 15 minutes from another LAN system, perhaps a r-pi.  If the ping doesn't work 2 times in a row, have an audio file played through some speakers to "clap" twice.  Wait 1 minute, then "clap" twice again.  The clapper would control the power plug for the modem/router.

There are more expensive solutions to this power control. A IoT Wyze power plug might work, but most IoT devices don't actually work when the internet is down, so you'll need something that only needs a LAN connection and accepts a REST command.

Or get 2 ISPs for the location and use a smart router.  I've seen cellular routers with SIMs for $150.  Think they have unlimited internet plans for $20/month each.  I know a guy that uses the $20 addon for each of his homes to hook up security camera systems for the mountain, beach, and ranch houses.

Also know in the US, t-mobile has a 5G device and plan for ~$50/month that includes everything you need.  [https://www.t-mobile.com/isp](https://www.t-mobile.com/isp) But you'll need a better router that would use the working ISP connection.  I know OPNSense and pfSense support that.

---

### Post by rsteinmetz70112 on 2021-08-26
HermanAB;

I have a box full of old dial up modems. I just have to go into the junk room and dig one out and make sure it works. :cool:.

TheFu :

The ISP can remote reboot the modem/router - I can even do that from their website, but it's not working.
After a reboot the modem/router is still showing an unspecified error. If I had a way around that I could see if the servers are up and if so possibly login and see what is going on. 

UPSs can also be controlled via USB from a working computer.

I'll have to look into options but I think a dial-up modem might work. It requires the phone lines to be up but so far that's not been an issue. I also have a number of wireless tablets on my cell account that don't cost a monthly fee that I might be able to rig up something.

I guess I'll add another project to my ever growing list. :(

---

### Post by scorp123 on 2021-08-26
> **rsteinmetz70112 said:**
> I have a remote location that is sometimes unmanned.   Occasionally I lose contact with the servers there and can't do any checking to find out what the problem is. Can anyone suggest a reasonable alternate method to circumvent the problem?

Install a router that supports "Failover" to a secondary / alternative connection?

At home I use this router:
[https://www.synology.com/en-global/products/RT2600ac]("https://www.synology.com/en-global/products/RT2600ac")

It has many "Pro" features I have not often seen in a default router firmware. Usually you'd need to flash something like OpenWRT to get such features.

Anyway, this router supports "Failover". Means you can use your WAN port as your "Main" Internet port and then another as "Failover". If your "Main" connection to Provider A goes down then the router will activate the "Failover" connection to Provider B.

And 3G/4G/LTE USB dongles are also supported.

In case a disaster strikes I probably would not route the whole network over the 4G dongle (this might be a bad idea and be very costly) ... but maybe and with a bit of scripting you could make it so that just 1 x Linux box dials out over this connection so you can SSH back in and take a look what's going on with your main connection?

Just an idea.

I was tinkering with the same idea for a while when my own Internet connection was very unstable due to nearby construction work. But that work is over and my Internet connection is extremely stable so I have not pursued the idea any further and actually implemented it.... but based on the research I did back then I know that this router model could do it.

---

